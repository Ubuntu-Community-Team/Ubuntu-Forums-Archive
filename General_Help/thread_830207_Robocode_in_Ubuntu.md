---
title: "Robocode in Ubuntu"
date: 2008-06-15
forum: General Help
---

### Post by thirddementia on 2008-06-15
Hey everyone, Im sorry for being a total noob; But after searching endlessly through the forums and web, I cant seem to find any package for robocode to install.  I dont have any idea what version or the steps to install robocode into my Hardy Heron 8.04 , so if anyone can help me get this thing running, I would appreciate it. (Maybe I shouldnt have slept through Unix Class.):)
With any luck and some help I can get my FSM ready for next weeks rumble.
Thanks everyone for anyone who can get me up and running.

---

### Post by y-lee on 2008-06-15
Open a terminal and type (copy and paste be better) the following two commands:

```
 wget http://downloads.sourceforge.net/robocode/robocode-setup-1.6.0.1.jar?modtime=1212452818&big_mirror=0
java -jar robocode-setup-1.6.0.1.jar
```

and follow the instructions on screen. :)

---

### Post by thirddementia on 2008-06-15
Y-lee, it look like it will go good but unfortunately; when i go to accept install; it freezes right up and will not let me accept options.
have we ever seen this behavior before?
Thank you so much for you reply; Ill send you some dynamic finite state machine code if I can get this running. :)

---

### Post by thirddementia on 2008-06-15
Wait that works.. I just had to get my java update and going :)

Thanks I owe you some FSM code :)

---

### Post by y-lee on 2008-06-15
> **thirddementia said:**
> Wait that works.. I just had to get my java update and going :)

Thanks I owe you some FSM code :)

:lolflag:

You know where to find me !!

Glad it worked, I'd never heard of Robocode before but I installed  it figuring this out for ya ;)

---

### Post by teakay on 2008-10-06
I succeed to install robocode .But when I try to open the compiler.Below message appear :

Please wait while Robocode sets up a compiler for you...
Setting up compiler for Windows XP
Java home is C:\Program Files\Java\jre1.6.0_07
Testing compile with javac...
javac does not exist.

And when i try to compile,command prompt show:
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
at javax.swing.ImageIcon.<init>(Unknown Source)
at javax.swing.ImageIcon.<init>(Unknown Source)
at sun.swing.WindowsPlacesBar.<init>(Unknow... Source)
at com.sun.java.swing.plaf.windows.WindowsF...
lder(Unknown Source)
at com.sun.java.swing.plaf.windows.WindowsF...
s(Unknown Source)
at javax.swing.plaf.basic.BasicFileChooserU... Source)
at com.sun.java.swing.plaf.windows.WindowsF...
n Source)
at javax.swing.JComponent.setUI(Unknown Source)
at javax.swing.JFileChooser.updateUI(Unknow... Source)
at javax.swing.JFileChooser.setup(Unknown Source)
at javax.swing.JFileChooser.<init>(Unknown Source)
at javax.swing.JFileChooser.<init>(Unknown Source)
at robocode.editor.EditWindow.fileSaveAs(Un... Source)
at robocode.editor.EditWindow.fileSave(Unkn... Source)
at robocode.editor.EditWindow.fileSave(Unkn... Source)
at robocode.editor.RobocodeEditor.saveRobot... Source)
at robocode.editor.RobocodeEditorMenuBar.fi...
Source)

pleasee..somebody help me

---

### Post by y-lee on 2008-10-06
**teakay** from the error messages you posted it looks like you are either using windows XP or you have installed a Robocode package intended for windows. So if you are using Ubuntu tell me how you installed Robocode and what package, source code or whatnot did you use, a link to the files would be appreciated.

If you are using windows I really can't help help you and you have posted in the wrong part of this forum, we have a section for windows problems and you will have better luck posting there.

And for future reference if you post long error messages please wrap the message in **code** tags like this: [noparse]```
 put code or error messages here
```[/noparse]. You can highlight the error messages or code and then click the **#** button above instead of typing the code tags directly if you wish.

---

### Post by teakay on 2008-10-06
y-lee,

Thankyou for the reply.Im sorry about the longcode. I have downloaded robocode version 1.6.1.2 from sourceforge.net.And it was installed successfully.But When i try to make MyFirstRobot by robocode editor. When robocode set compiler following message show up :
Please wait while Robocode sets up a compiler for you...

Setting up compiler for Windows XP
Java home is C:\Program Files\Java\jre1.6.0_07

Testing compile with javac...
javac does not exist.

Extracting Jikes...
Jikes extracted successfully.

Testing compile with Jikes...
Jikes ok.

Congratulations!  Compiler set up successfully.
Click OK to continue.

It said javac does not exist, but i think the class path setup  correctly.
Is there something wrong with my javaRE? or else?

---

### Post by y-lee on 2008-10-06
It still appears to me you are using windows XP, you didn't answer that in your last post. The error message below is a error message for windows.

```
Setting up compiler for Windows XP
Java home is C:\Program Files\Java\jre1.6.0_07

Testing compile with javac...
javac does not exist.
```


Now i looked once again at the Robocode web site site(sourceforge) and saw the jar package and source code both are platform independent so however you have installed it it shouldn't matter whether you are using windows or linux. But i**f you are using windows **please post your problem in the [windows Discussion]("http://ubuntuforums.org/forumdisplay.php?f=170") part of this forum, link back to your post here if you wish... I would :)

Now if you are using ubuntu then i suspect part of the reason for the errors you are getting is that you either have jikes installed or robocode itself is using it, installing it or something.

```
Extracting Jikes...
Jikes extracted successfully.

Testing compile with Jikes...
Jikes ok.
```

According to [wikipedia]("http://en.wikipedia.org/wiki/Jikes")

> Jikes is an open source Java compiler written in C++. It is no longer being updated....Unfortunately, as no further versions were released since, Java SE 6 is not supported.


This could conceivably cause problems, so if you are using ubuntu uninstall jikes if you don't need it. After that you can open a terminal and try the following commands, I am not at all sure they are all necessary but if they run successfully then you should have java properly set up.

```
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```

Next, edit the JVM configuration file


```
sudo -b gedit /etc/jvm
```

and add the following to the top of the file

```
/usr/lib/jvm/java-6-sun
```

---

### Post by drubin on 2008-10-06
> **teakay said:**
> y-lee,

Thankyou for the reply.Im sorry about the longcode. I have downloaded robocode version 1.6.1.2 from sourceforge.net.And it was installed successfully.But When i try to make MyFirstRobot by robocode editor. When robocode set compiler following message show up :
Please wait while Robocode sets up a compiler for you...

Before answering/asking any more question are you using Ubuntu or Windows or some other distro of linux?

Next please post the output of 
```
java --version
javac --version
```

Once you have done both those things we will be able to accurately  help you.

---

### Post by teakay on 2008-10-06
Im really sorry, yes I'm using windows xp...coz i reply your question half asleep in midnight;p so I didnt answer it well;p. I'll go to windows forum.
Thanks anyway

---

### Post by drubin on 2008-10-07
> **teakay said:**
> Im really sorry, yes I'm using windows xp...coz i reply your question half asleep in midnight;p so I didnt answer it well;p. I'll go to windows forum.
Thanks anyway

That is ok we all understand. 
This might help you
[http://www.java.com/en/download/help/path.xml](http://www.java.com/en/download/help/path.xml)  You will have to change the version numbers to suite your needs

---

### Post by Moyamo on 2010-06-29
There was a new version of robocode out and it wasn't available through the synaptic package manager so i installed it manually.  But no it doesn't have a config folder and when i close the app it loses all the settings i changed what should i do?

---

