---
title: "Packaging a Python program for a ubuntu distribution ."
date: 2013-02-06
forum: General Help
---

### Post by Raafat1991 on 2013-02-06
Hi guys...i want to know how can i package a Python program for installing it on a ubuntu distribution .

clearly

assuming i have :

```
#!/usr/bin/python
# *-* encoding:utf8 *-*  
 
import sys
from PyQt4 import QtGui
   
class Window(QtGui.QWidget):
  def __init__(self,parent=None):
    
    super(Window,self).__init__()
    self.setWindowTitle('Window')
    self.resize(300,300)
    
    Label=QtGui.QLabel('Enter your name:',self)
    self.entryLine=QtGui.QLineEdit(self)
    self.entryLine.move(120,0)
    
    
def RunIt():
  Application=QtGui.QApplication(sys.argv)

  myApp=Window()
  myApp.show()
  Application.exec_()

  

if __name__=='__main__':
  RunIt()


```how can i package that code for later i can install it by typing : 

```
apt-get install myCode
```thank you...

---

### Post by Raafat1991 on 2013-02-11
Hi...any idea

---

