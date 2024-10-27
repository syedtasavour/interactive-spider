# Interactive Spider Web Animation

A mesmerizing web-based animation that creates an interactive spider web effect following the user's cursor. This effect involves multiple spider-like entities generating dynamic web patterns that respond fluidly to mouse movement.

## Features

- **Spider Entities**: Multiple spiders that follow the user's cursor.
- **Dynamic Web Patterns**: The spiders dynamically create web-like patterns.
- **Smooth Animation**: Noise-based line distortion for organic movement.
- **Responsive Design**: Adjusts to window size.
- **Dark Theme**: Dark background with white web patterns.

## Technical Implementation

### Core Components

#### Spider Entity
- Created using the `spawn()` function.
- Each spider entity has:
  - **Position**: (x, y) coordinates.
  - **Target Position**: (tx, ty) following the cursor.
  - **Movement Parameters**: (kx, ky) to control speed and direction.
  - **Walk Radius**: Allows autonomous wandering.
  - **Point Collection**: Generates points for web formation.

#### Web Pattern Generation
- Utilizes two main point collections:
  - **Main Points**: 333 randomly distributed points.
  - **Circular Points**: 9 points in a circular arrangement.
- **Web Lines**: Drawn using linear interpolation (lerp) with noise-based distortion.

### Key Functions

- **spawn()**: Generates a spider entity with:
  - Random web vertices (333 points) and circular structure points (9 points).
  - Random initial position and movement parameters.
- **drawLine(x0, y0, x1, y1)**: Creates a distorted line between points with 100 intermediate points, using noise displacement.
- **noise(x, y, t)**: Generates smooth, sine-based noise values for complex spider movement.
- **lerp(a, b, t)**: Smooth transition function for values between a and b.
- **many(n, f)**: Helper function to create arrays of repeated elements.
- **drawCircle(x, y, r, color)**: Draws spider bodies and nodes in the web.

### Animation Loop

1. Sets canvas size on window resize.
2. Clears canvas and draws a black background.
3. Updates spider positions.
4. Draws the interactive web pattern.
5. Runs at the display's refresh rate.

### Event Handling

- **Pointer Movement Tracking**: Adjusts spider target positions for smooth tracking.
- **Independent Spider Tracking**: Each spider entity follows the cursor independently.

### Customizable Parameters

- **Number of Spiders**: `many(2, spawn)`
- **Points per Spider**: `many(333, ...)`
- **Web Size**: `innerWidth / rnd(100, 150)`
- **Movement Speed**: `min(innerWidth/100, (fx - x)/10)`
- **Line Density**: `many(100, ...)`

