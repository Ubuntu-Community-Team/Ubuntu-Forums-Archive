---
title: "AttributeError: 'module' object has no attribute 'MyStuffx'"
date: 2012-10-21
forum: General Help
---

### Post by workaround on 2012-10-21
```

#file script.py
 #File "/home/test/Documents/cript.py"
 import myclass01
 import myclass02
 import MyStuff

 mc = myclass01.MyClass1() 
 print "What\'s this " + mc.x + "?"
 print "How about this? ", mc.printsomething()

 mc2 = myclass02.MyClass2()
 print "this is ", mc2.printsomething()

 # MyStuff is a module. It contains class MyStuffx. 
 #      This class contains method apple
 #from MyStuff import apple  # does not work
 #print "this is apple ", apple()
 # 
 #  File "/home/test/Documents/script.py"
 ms = MyStuff.MyStuffx()
 print "this is apple ",ms.apple
#-------------------------------------------------------//

#  File "/home/test/Documents/pymodules/MyStuff.py"
class MyStuffx:  # (object): how this works, who knows?    
    def __init__(self):
         self.tangerine = 'And now a thousand years between'
 
     def apple(self):
         print 'I AM CLASSY APPLES!'

#-------------------------------------------------------//
#  File "/home/test/Documents/pymodules/myclass01.py"
 class MyClass1:
     def __init__(self):
         self.x = 'c1'
               
     def printsomething(self):
         print 'hey'


#-------------------------------------------------------//
#  File "/home/test/Documents/pymodules/myclass02.py"
 class MyClass2:
     def __init__(self):
         self.x = 'c2'
         
     def printsomething(self):
         print 'crap2'

#-------------------------------------------------------//
# the errors I am getting
'import sitecustomize' failed; use -v for traceback
What's this c1?
How about this?  hey
None
this is  crap2
None
Traceback (most recent call last):
  File "/home/peshone/Documents/script.py", line 42, in <module>
    ms = MyStuff.MyStuffx()
AttributeError: 'module' object has no attribute 'MyStuffx'


```
Would someone know how to resolve the errors?
Thanks

---

