---
title: "Colored QPushbutton with pyqt5??"
date: 2020-10-12
forum: General Help
---

### Post by RockDoctor on 2020-10-12
I'm trying to change the background color of a QPushButton in my application. The code below works properly in Fedora, but in Ubuntu 2010 the button remains uncolored. Am I doing something wrong that just happens to work in Fedora, or is it an Ubuntu problem?  Thanks.
```
if bad_word_flag:
                self.btn_color_check.setStyleSheet("background-color: red")
            else:
                self.btn_color_check.setStyleSheet("background-color: green")

```

---

### Post by norobro on 2020-10-12
No help, but it works fine in a constructor and a slot on 20.04.```
$ pip3 list | grep -i pyqt5
PyQt5                  5.15.1              
PyQt5-sip              12.8.1
```

---

### Post by RockDoctor on 2020-10-13
Looks like it might be a bug in the Ubuntu python3-pyqt5 package. On 20.04, I get 
```
~$ pip3 list | grep -i pyqt5
PyQt5                  5.14.1
```
```
~$ dpkg -l | grep -i pyqt5
ii  python3-pyqt5                                 5.14.1+dfsg-3build1                  amd64        Python 3 bindings for Qt5

```

---

### Post by norobro on 2020-10-13
I installed the Ubuntu python3-pyqt5 package and my simple example still works.```
$ pip3 list | grep -i pyqt5
PyQt5                  5.14.1              
PyQt5-sip              12.8.1 


$ dpkg -l | grep -i pyqt5
ii  python3-pyqt5                                 5.14.1+dfsg-3build1 
```My test code:```
#!/usr/bin/python3


'''
    execute with a zero (false) or  another integer (true) to test the if statement in the ctor.
    click the button to test the slot if
'''
from PyQt5 import QtWidgets
from PyQt5.QtCore import pyqtSlot
import sys


class pushButton(QtWidgets.QPushButton):
    flag = 0
    def __init__(self, f, parent=None):
        self.flag = f
        super(pushButton, self).__init__(parent)
        self.setText("Push Me") 
        self.clicked.connect(self.change_color)
        if int(self.flag):
            self.setStyleSheet("color:white;background-color:green;")
        else:
            self.setStyleSheet("color:white;background-color:red;")
            
    @pyqtSlot()
    def change_color(self):
        if int(self.flag):
            self.setStyleSheet("color:black;background-color:white;")
        else:
            self.setStyleSheet("color:white;background-color:gray;")
        self.flag = not self.flag
 
if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    if len(sys.argv) == 1:
        print("usage: ./filename integer")
        exit()
    pb = pushButton(sys.argv[1])
    pb.show()
    app.exec_()
```Hope this helps.

---

### Post by RockDoctor on 2020-10-14
Your code properly sets the foreground color, but not the background color. 

Rephrased my question and re-googled, finding this: [https://forum.qt.io/topic/51222/solved-can-t-set-background-color-of-a-qpushbutton/2](https://forum.qt.io/topic/51222/solved-can-t-set-background-color-of-a-qpushbutton/2) Setting the border, even to none, does the trick. ```
        if int(self.flag):
            self.setStyleSheet("color:blue;background-color:green;border:none;")
        else:
            self.setStyleSheet("color:yellow;background-color:red;border:none;")
```
Thanks for the help!

---

