---
title: "How to install / use MrPostman with Thunderbird"
date: 2005-07-03
forum: General Help
---

### Post by oliwally on 2005-07-03
I'm trying to download my hotmail using Thunderbird and MrPostman. I did this in WinXP and it works beaut, but I'm having a few probs here in Kubuntu.

This is what I have done so far

[list]I have installed java-gcj-compat - not sure if this was needed
I have downloaded MrPostman-20050626.jar
I can run MrPostman by entering "java -jar MrPostman-20050626.jar" in the shell while in the directory where I saved MrPostman. Gui comes up  - seems to work.
MrPostman does connect to the net. I know 'cause I asked it to update the scripts and it did.
I created a new account in Thunderbird, with the Pop server being "localhost" at port 11110
[/list]

However, when attempting to download mail nothing seems to happen. Thunderbird is telling me that it's connecting to localhost - and that's it. It just sits there.

Can anyone help? What do I still have to do to make it work?

Also, how do I do it so that MrPostman starts at bootup / login and runs in the background without the gui coming up ? Although, I don't really care if the gui comes up or not.

Please help.

**EDIT 23-7-05 - A SOLUTION AFTER ALL WAS SAID AND DONE**

There is no solution about making MrPostman work in this topic, but there is a solution to getting to your hotmail by using something other than MrPostman. Go to [http://webmail.mozdev.org/](http://webmail.mozdev.org/) and follow the instructions. Very easy to use.

---

### Post by desdinova on 2005-07-03
[QUOTE=oliwally]I'm trying to download my hotmail using Thunderbird and MrPostman. I did this in WinXP and it works beaut, but I'm having a few probs here in Kubuntu.

This is what I have done so far


[list]
[*]I have installed java-gcj-compat - not sure if this was needed
 
I have downloaded MrPostman-20050626.jar
 
I can run MrPostman by entering "java -jar MrPostman-20050626.jar" in the shell while in the directory where I saved MrPostman. Gui comes up - seems to work.
 
MrPostman does connect to the net. I know 'cause I asked it to update the scripts and it did.
 
I created a new account in Thunderbird, with the Pop server being "localhost" at port 11110
[/list]
However, when attempting to download mail nothing seems to happen. Thunderbird is telling me that it's connecting to localhost - and that's it. It just sits there.

Can anyone help? What do I still have to do to make it work?

Also, how do I do it so that MrPostman starts at bootup / login and runs in the background without the gui coming up ? Although, I don't really care if the gui comes up or not.

Please help.[/QUOTE]

 From the Gnome Menu - System - Settings - Sessions you can set an app to start up as required

---

### Post by oliwally on 2005-07-03
Thank you for replying.
>  From the Gnome Menu - System - Settings - Sessions you can set an app to start up as required

Would you know how to do this in KDE ? I'm using Kubuntu. I tried Control Center - KDE Components etc, but I can't find the appropriate option to add MrPostman.

Also, what else do I need to do to make it work?

---

### Post by oliwally on 2005-07-04
Well, I've worked out the automatic starting thing. Here is what I did:

Open Konqueror - Go - Autostart. Right-click in that folder and Create New - Link to Application. Give it a name (MrPostman). In the Application Tab, name it again; in the 'Command' field typed 'java -jar MrPostman-20050626.jar' (or whatever the MrPostman version is), and in the 'Work Path' field navigated to the folder where the MrPostman download stored. It works. There is even an option in MrPostman not to run the Gui when the program is started. 

I'm sure it's not the most elegant way of doing it, and you still have copy of MrPostman showing in the panel, but it's all I know. If anyone knows how to let it run invisible in the backgroung - I'd love to know.

But I still can't get Thunderbird to download email using MrPostman ! HELP PLEASE!


EDIT

Hmm....seems like unticking the 'run Gui when MrPostman starts' doesn't work

---

### Post by oliwally on 2005-07-06
Could anyone help Please !!! O:)

---

### Post by manicka on 2005-07-06
switch to ubuntu/gnome  :-P  ... sorry, couldn't resist :)

---

### Post by oliwally on 2005-07-06
Why ? Does Gnome sort such problems out? Does it work in Gnome ? If so, then how?

---

### Post by manicka on 2005-07-06
To be honest I have no idea, but it might be worth a try.

I was just offering a simple solution to your KDE problems ;)

---

### Post by oliwally on 2005-07-06
Could anyone shed some light on this issue ?

---

### Post by manicka on 2005-07-06
okay, you made me curious and I checked out mrpostman. I have it working well here using evolution.

I think your problem must be with your thunderbird settings. When you entered your username did you use your full email address. Which webmail are you trying to connect to? hotmail?

Some web based mail like gmail have support for pop access anyway so a program like this would be unnecessary.

Also, in the postman program itself I checked the box that says 'allow other hosts to use MrPostman', don't know if this makes a difference or not.

After you get it up and running you should be able to autostart mrpostman by creating a application link icon then placing this in your kde autostart folder (autostart is inside the .kde folder in your home directory). Sorry, it's been a while since I've used KDE so I can't remember the exact procedure. Right click on desktop and choose New-->ApplicationLink or something like that then add in a command to start mrpostman. Basically you'd initiate mrpostan with a command like '```
java -jar home/*usernam*e/.mrpostman/MrPostman-20050626.jar 
(I placed my files in a folder called .mrpostman inside my home directory)
or 
java -jar /*pathto/yourdirectory*/MrPostman-20050626.jar.
``` That's the command to start it in gnome, not sure if the same will work in kde- should do

Anyway once you're happy with the way things are working you should be able to uncheck the button that says 'Run the GUI when the program starts' and it should just run in the background. Not sure how you get the gui back after doing this so make sure it's all working properly first.

HTH

---

### Post by manicka on 2005-07-06
bah... just started a new session and now it won't work and I'm getting a password error when checking mail.

Good luck with it, it seems a bit to buggy for me.

---

### Post by morphodone on 2005-07-06
so did you get mr postman working?

i have been using it for the last few months for hotmail with mepis linux and kde...
i made a shell script to run the program that sits on my desktop
i just hide the gui when it pops up [file -> close gui].  if i happen to reboot i just double click the icon again, but i don't reboot that often.

when the gui starts just click on the modules tab and make sure your module is listed there
i wouldn't set it to hide the gui automatically, b/c it's difficult to get the gui
back and you won't be able to troubleshoot

good luck

---

### Post by oliwally on 2005-07-07
Thanks so much for helping out. Haven't been able to get to my computer for a day, hence the late reply.

> I think your problem must be with your thunderbird settings. When you entered your username did you use your full email address. Which webmail are you trying to connect to? hotmail?

Yes and yes

> Also, in the postman program itself I checked the box that says 'allow other hosts to use MrPostman', don't know if this makes a difference or not.

Has made no difference

> After you get it up and running you should be able to autostart mrpostman by creating a application link icon then placing this in your kde autostart folder....

Have done this  - autostart works. Thank You

> uncheck the button that says 'Run the GUI when the program starts' and it should just run in the background

Doesn't work, but that's okay.

No, it's still not working for me.  ](*,)  It doesn't even ask me for a password. It seems like I'm not even getting through to hotmail.

---

### Post by oliwally on 2005-07-10
Bump

---

### Post by oliwally on 2005-07-11
Does anyone know how to make MrPostman work ?

---

### Post by manicka on 2005-07-11
just a thought... Have you logged into your hotmail account recently to see if it's still functional.

---

### Post by oliwally on 2005-07-13
Yes, it's still working - I use it all the time !

Has anybody got MrPostman working? Which version are you using? Is anybody using other software to get to their hotmail through Thunderbird?

---

### Post by oliwally on 2005-07-14
Bump

---

### Post by morphodone on 2005-07-14
[QUOTE=oliwally]Yes, it's still working - I use it all the time !

Has anybody got MrPostman working? Which version are you using? Is anybody using other software to get to their hotmail through Thunderbird?[/QUOTE]


yep, i am using version 1.1 with kde

downloaded from [here](http://sourceforge.net/project/showfiles.php?group_id=68124) 

once installed be sure to update the scripts by hitting the update scripts button

and follow the online documentation for getting thunderbird setup correctly

---

### Post by oliwally on 2005-07-15
Thanks for replying. 

I'm using version 1.2RC1. Perhaps there is a problem with that version ? I'll try 1.1 and see how I go.

So, how are you making your MrPostman run? What command do you use ? Are you doing the same as me (see above) ?

---

### Post by oliwally on 2005-07-15
I'm now running version 1.1 but still no luck.

When updating the scripts I get an error saying 'there was an error. Please see log' or similar. When having a look at the log it's empty. Also, when clicking on help and 'using MrPostman' it's just empty - there is nothing there. I wonder if I've actually got MrPostman running correctly ? This is what I did:
> 
Open Konqueror - Go - Autostart. Right-click in that folder and Create New - Link to Application. Give it a name (MrPostman). In the Application Tab, name it again; in the 'Command' field typed 'java -jar MrPostman-20050626.jar' (or whatever the MrPostman version is), and in the 'Work Path' field navigated to the folder where the MrPostman download stored

Morphodone - you've got yours working. Can you please give me a detailed description of how you have made MrPostman run (not how to configure Thunderbird - I'm quite sure I've got that right).

---

### Post by oliwally on 2005-07-17
Can't anybody give me a solution ?  ......please !

---

### Post by morphodone on 2005-07-17
[QUOTE=oliwally]Can't anybody give me a solution ?  ......please ![/QUOTE]

okay i'll post a couple of screen pics of how to get it working...

---

### Post by morphodone on 2005-07-17
okay here you go

[tutorial](http://home.comcast.net/~morphodone/mrpostman/)

WARNING - MANY PICTURE FILES!!!

---

### Post by oliwally on 2005-07-18
Thank you so much for going through all that trouble - you're tops !

I'm one step closer. For starters, I had the wrong package downloaded. I wasn't using the 'install-mrpostman....'. rather I was just using the 'MrPostman....' package

Now when I did do the 'java -jar install-mrpostman-20050626.jar', the starting screen came up but the language option wasn't working too well (it was greyed out). I also received the following error:
```

(.:8188): Gdk-CRITICAL **: gdk_window_get_origin: assertion `window != NULL' failed
- Error -
java.lang.Exception: installation canceled
java.lang.Exception: installation canceled
   at com.izforge.izpack.installer.GUIInstaller.loadLangPack() (Unknown Source)
   at com.izforge.izpack.installer.GUIInstaller.GUIInstaller() (Unknown Source)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at com.izforge.izpack.installer.Installer.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
```

I'm beginning to think that the Java runtime environment on my computer is not working as it should.

I have used Synaptic to install the following java packages:

[INDENT]sun-j2re1.5  Java(TM) 2 RE, - Standard Edition, Sun Microsystems(TM)
java-common - Base of all Java packages
java-gcj-compat- Java runtime environment with GCJ[/INDENT]


Am I missing something ?

---

### Post by oliwally on 2005-07-19
Help me Obi Wan. You're my only hope.

---

### Post by morphodone on 2005-07-20
I don't know why you got those errors ](*,) 

You might want to submit a post at the mrpostman forum...[here](http://sourceforge.net/forum/?group_id=68124) 

maybe they can help :roll:

---

### Post by oliwally on 2005-07-21
Ok, thanks for that and thanks for your help so far. Really appreciate it - I made some headway at least. If I find a solution I will post it here.

---

### Post by oliwally on 2005-07-22
Ok, problem solved. The answer is in using something other than MrPostman.

I have just installed a webmail plugin for Thunderbird - workes without any problems so far. Very easy to install, nothing to worry about. You can find it at [http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Thanks everyone for helping out.

---

### Post by morphodone on 2005-07-22
glad to see you found a solution

if my mrpostman breaks i'll try that... \\:D/

---

### Post by manicka on 2005-07-22
great news! I'm glad you found a solution for this one :)

---

