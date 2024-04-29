```python
def getWindowPositionTypeFullBrowser(num_browsers: int, width_browser: int, height_browser: int, distance: int):
    """distance là khoảng cách giữa các cửa số với nhau"""
    w = width_browser
    h = height_browser
    width_screen, height_screen = ctypes.windll.user32.GetSystemMetrics(
        0), ctypes.windll.user32.GetSystemMetrics(1)
    x = - (width_browser + distance)
    y = 0
    position = []
    for i in range(num_browsers):
        x += width_browser + distance
        if x+width_browser > width_screen:
            x = 0
            y += height_browser + distance
        if (height_browser/2) >= (height_screen - (y + distance)):
            y = 0
            x = 0
        position.append({'index': i, 'x': x, 'y': y, 'width': w, 'height': h})
    return position


def getWindowPositionTypeStack(num_browsers: int, width_browser: int, height_browser: int, distance: int):
    """distance là đoạn xếp chồng cửa sổ lên nhau"""
    w = width_browser
    h = height_browser
    width_screen, height_screen = ctypes.windll.user32.GetSystemMetrics(
        0), ctypes.windll.user32.GetSystemMetrics(1)
    distance_heigh = 5
    x = - distance
    y = 0
    position = []
    for i in range(num_browsers):
        x += distance
        if x+width_browser > width_screen:
            x = 0
            y += height_browser + distance_heigh
        if (height_browser/2) >= (height_screen - (y + distance)):
            y = 0
            x = 0
        position.append({'index': i, 'x': x, 'y': y, 'width': w, 'height': h})
    return position
```
