# MDP REPRESENTATION

## AIM:

To model the movement of a robot vacuum cleaner in a 2-room environment using Markov Decision Process (MDP).

## PROBLEM STATEMENT:

### Problem Description
A robot vacuum cleaner moves between two rooms (Room 0 and Room 1). It can CLEAN the room or MOVE to the other room. Each action gives a reward: cleaning a dirty room gives +10, moving has a cost of -1, and trying to clean an already clean room gives 0.

### State Space

States represent the location of the robot and cleanliness of each room: (robot_location, room0_status, room1_status)
robot_location = 0 (Room 0) or 1 (Room 1)
room_status = 0 (dirty) or 1 (clean)

### Sample State

(0, 0, 1) → Robot is in Room 0
1. Room 0 is dirty
2. Room 1 is clean.

### Action Space

0 → CLEAN
1 → MOVE

### Sample Action

1. CLEAN → Cleans the current room
1. MOVE → Moves to the other room

### Reward Function

1. CLEAN dirty room → +10
2. CLEAN clean room → 0
3. MOVE → -1

### Graphical Representation

<img width="1536" height="1024" alt="RL img" src="https://github.com/user-attachments/assets/ab3f75b8-da3e-428f-b464-0cdc874cc37e" />


## PYTHON REPRESENTATION:
```
Name: VINOTH M P
Reg No: 212223240182
# Robot Vacuum Cleaner MDP
P = {
    (0, 0, 0): {  # Robot in Room 0, both rooms dirty
        0: [(1.0, (0, 1, 0), 10, False)],  # CLEAN Room0
        1: [(1.0, (1, 0, 0), -1, False)]   # MOVE to Room1
    },
    (0, 1, 0): {  # Robot in Room 0, Room0 clean, Room1 dirty
        0: [(1.0, (0, 1, 0), 0, False)],   # CLEAN Room0 already clean
        1: [(1.0, (1, 1, 0), -1, False)]   # MOVE to Room1
    },
    (1, 0, 0): {  # Robot in Room1, both rooms dirty
        0: [(1.0, (1, 0, 1), 10, False)],  # CLEAN Room1
        1: [(1.0, (0, 0, 0), -1, False)]   # MOVE to Room0
    },
    (1, 0, 1): {  # Robot in Room1, Room0 dirty, Room1 clean
        0: [(1.0, (1, 0, 1), 0, False)],   # CLEAN Room1 already clean
        1: [(1.0, (0, 0, 1), -1, False)]   # MOVE to Room0
    },
    (0, 1, 1): {  # Both rooms clean, Robot in Room0
        0: [(1.0, (0, 1, 1), 0, True)],    # CLEAN → terminal
        1: [(1.0, (1, 1, 1), -1, True)]   # MOVE → terminal
    },
    (1, 1, 1): {  # Both rooms clean, Robot in Room1
        0: [(1.0, (1, 1, 1), 0, True)],    # CLEAN → terminal
        1: [(1.0, (0, 1, 1), -1, True)]   # MOVE → terminal
    }
}

print(P)
```

## OUTPUT:
```
{(0, 0, 0): {0: [(1.0, (0, 1, 0), 10, False)], 1: [(1.0, (1, 0, 0), -1, False)]}, 
 (0, 1, 0): {0: [(1.0, (0, 1, 0), 0, False)], 1: [(1.0, (1, 1, 0), -1, False)]},
 (1, 0, 0): {0: [(1.0, (1, 0, 1), 10, False)], 1: [(1.0, (0, 0, 0), -1, False)]},
 (1, 0, 1): {0: [(1.0, (1, 0, 1), 0, False)], 1: [(1.0, (0, 0, 1), -1, False)]},
 (0, 1, 1): {0: [(1.0, (0, 1, 1), 0, True)], 1: [(1.0, (1, 1, 1), -1, True)]},
 (1, 1, 1): {0: [(1.0, (1, 1, 1), 0, True)], 1: [(1.0, (0, 1, 1), -1, True)]}}
```

## RESULT:
Thus, the robotic vaccum cleaner problem is successfully represented in MDP form.

