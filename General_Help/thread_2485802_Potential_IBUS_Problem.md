---
title: "Potential IBUS Problem"
date: 2023-04-10
forum: General Help
---

### Post by rwe061 on 2023-04-10
Ubuntu 22.04

I am trying to track down a problem that I first noticed using python with pyside6 (QT6).  I am not sure how it is all related.

ibus-setup shows this error message:

> (ibus-setup:13910): Gdk-CRITICAL **: 08:07:42.801: gdk_wayland_window_set_dbus_properties_libgtk_only: assertion 'GDK_IS_WAYLAND_WINDOW (window)' failed


I get this python error/warning:

> qt.dbus.integration: Could not connect "org.freedesktop.IBus" to globalEngineChanged(QString)

Here is my simple sufficient program that shows the issue.

```
from PySide6.QtWidgets import QApplication, QMainWindow

app = QApplication()

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("My App")

window = MainWindow()
window.show()
app.exec()

```

I need some direction for troubleshooting this.

Thanks

rich

---

### Post by r-aluizio on 2023-04-12
Just adding to the post. I'm having the same issue when using pyside6.

---

### Post by MAFoElffen on 2023-04-12
First, make sure ibus is loaded and there is a connection to it... That you can talk to it and that it talks back.
```

ibus read-cache
dbus-send --system --print-reply --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.ListNames
echo $QT_IM_MODULE

```
If not, restart ibus and try again...
```

ibus restart

```
Then, if all is well,  try a more basic, simpler QT example
```

import QtQuick
import QtQuick.Window
    
Window {
    width: 640
    height: 480
    visible: true
    title: qsTr("Hello World")

    Text {
        text: qsTr("Hello World")
        anchors.centerIn: parent
        {
}

```

---

### Post by rwe061 on 2023-04-13
Thanks for the response. 

I simplified the python program, not easily able to do exactly what you suggested.  This issue isn't really causing a problem in running programs.  I just like to clear up error messages.

When I get the error message, Ibus-daemon is running and restarting it doesn't help.  

If I 'end' the ibus-daemon, the error message does not appear.  The QT system probably discovers there is no ibus running, so does not try to connect to it, so no error message.

I think this might be a QT6 problem, not a linux problem.  So, I decided to ignore it for now, or maybe describe it on a QT forum.

```
from PySide6.QtWidgets import QApplication

app = QApplication()
app.exec()


```

---

### Post by chris-mayo on 2023-05-04
QtBase fix: [https://code.qt.io/cgit/qt/qtbase.git/commit/?id=9d031caf09b2c14328268ef0e871efd30e80eab2](https://code.qt.io/cgit/qt/qtbase.git/commit/?id=9d031caf09b2c14328268ef0e871efd30e80eab2)

---

### Post by rwe061 on 2023-05-05
Thanks for that update

---

