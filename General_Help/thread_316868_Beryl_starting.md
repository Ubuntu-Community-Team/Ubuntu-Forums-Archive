---
title: "Beryl starting"
date: 2006-12-11
forum: General Help
---

### Post by Cikrum on 2006-12-11
Hello,
I was wondering why my beryl settings manager won't start up. I used this tutorial   [http://www.ubuntuforums.org/showthread.php?p=1872761#post1872761](http://www.ubuntuforums.org/showthread.php?p=1872761#post1872761)
and now when I try to start the app it doesn't begin. It seems to be installed fine.

---

### Post by Hurons on 2006-12-11
I have the same issue.

Anyone?

Thank You

---

### Post by NumberOne on 2006-12-11
Go to System > Preferences > sessions, and put these 2 statements in your startup window.  

beryl --display :0 &
emerald --replace &

HTH
Tony

---

### Post by Cikrum on 2006-12-11
Hello 
Thanks for the reply and I now have the Beryl system manager working. I went into synaptic package manager and it told me I had broken packets so after those were fixed It began to work fine. I also put in the commands you mentions in to the into the sessions under startup programs (is this the correct spot). I am now just unsure where to open or begin using Beryl. I tryed just typeing in Beryl in terminal but it told me no composite extension. I am some what lost on what to do.
Thx 
Cikrum

---

### Post by NumberOne on 2006-12-11
Just logout and log back in and Beryl should start automatically.
T.

---

### Post by Cikrum on 2006-12-12
The login and out didn't work and it didn't start automatically. I haven't really told it to start automatically seeing as how I don't know how to. A friend of mine told me I to start up on a different session. Is that true?
Thx 
Cikrum

---

### Post by TheRingmaster on 2006-12-12
> **Cikrum said:**
> The login and out didn't work and it didn't start automatically. I haven't really told it to start automatically seeing as how I don't know how to. A friend of mine told me I to start up on a different session. Is that true?
Thx 
Cikrum
see post three

---

### Post by Cikrum on 2006-12-12
I put those 2 commands under preferences> sessions> startup programs is this the correct area. If so it doesn't work. I have the command correct I checked and it doesn't start up. Do I need to start under and different session?
Thx
Cikrum

---

### Post by xpod on 2006-12-12
Alt-f2 then typing "beryl-manager" does it for me.

---

### Post by DarkN00b on 2006-12-12
I just put a launcher button on my bottom panel that runs beryl-manager.

---

### Post by bulldog on 2006-12-12
I have set beryl-manager in the sessions menu,so it will start when edgy start.

---

### Post by Cikrum on 2006-12-12
Thx for the replies,
I just want to clarify, beryl settings manager is not the problem for me I can run this fine. The major problem I am having is with just using beryl and having it do its stuff. I also want to clairfy I am using Dapper.
Thx 
Cirkum

---

### Post by bulldog on 2006-12-12
Open the beryl-settings-manager and take a look to the possibility's.
You have to test things for your self,what you like and what not.

---

### Post by Cikrum on 2006-12-12
Well, I have finally got beryl-manager working...sort of. It says that i am using beryl and it says that it starts up with my computer, but nothing has changed. I see no difference. I have used the setting manager and I have turned on Beryl animations and other such things but I dont have any effects changed on the computer. Am I missing some important detail. I awsume there is.
Thx Cikrum

---

### Post by bulldog on 2006-12-12
You should see the Beryl splash at start up.
Can you choose a window decorator?
Should be listed two of them,Beryl and Metacity,choose beryl and see if it starts.

You should have the red diamant in the notification box,so you can choose from there.

---

### Post by Cikrum on 2006-12-12
I choose the beryl, when I start beryl manager(off the two choices) but nothing happens still. And Sorry newb question but what is the notiffication box? Is this like windows system tray...if so i deleted mine. ](*,) 
As for the windows decorator It is Emerld. Pretty sure I got this early in an attempt to get beryl.

Thx 
Cikrum

---

### Post by TheRingmaster on 2006-12-12
> **Cikrum said:**
> I choose the beryl, when I start beryl manager(off the two choices) but nothing happens still. And Sorry newb question but what is the notiffication box? Is this like windows system tray...if so i deleted mine. ](*,) 
As for the windows decorator It is Emerld. Pretty sure I got this early in an attempt to get beryl.

Thx 
Cikrum
The notification box tells you if you have any updates or you need to restart. to put it back there: right-click on where it used to be in the panel and choose "add to panel". From there you can choose the notification box.

---

### Post by Cikrum on 2006-12-12
Ok, thank you very much, you have no idea how long i have been trying to get that back :) any way I now can see the beryl in the noticfication area. I can Change setting on it aswell. I am using the beryl windows manager and the emerald windows decorator. Is there anything i need to change for the advanced tab?
Thx 
Cikrum

---

### Post by TheRingmaster on 2006-12-12
> **Cikrum said:**
> Ok, thank you very much, you have no idea how long i have been trying to get that back :) any way I now can see the beryl in the noticfication area. I can Change setting on it aswell. I am using the beryl windows manager and the emerald windows decorator. Is there anything i need to change for the advanced tab?
Thx 
Cikrum
I think that you are all set now. Just play around with the settings to see what you like best. you can always go back to default if you venture too far.

---

### Post by Cikrum on 2006-12-12
The only problem is that nothing happens. I have all the setting (like flame when close window but nothing happens. Is there something I need to turn on.
Thx Cikrum

---

### Post by TheRingmaster on 2006-12-13
> **Cikrum said:**
> The only problem is that nothing happens. I have all the setting (like flame when close window but nothing happens. Is there something I need to turn on.
Thx Cikrum
if you have already put _beryl-manager_ in your start up programs list, then all you need to do is press ctrl-alt-backspace --or-- restart you computer for it to get up and running.
 
ps. You don't have to put the emerald theme manager in your start-up list for it to work.

---

### Post by Cikrum on 2006-12-15
Hello,
I believe this is the problem. When i press Ctrl-Alt-Backspace all of my open windows close and it gives me a black screen ie. terminal I believe and once I wait a few seconds it returns me to the login screen. I Have no idea what the problem is, Although it might be my resolution. Any Ideas??
Thx,
Cikrum
Edit--Stupid me its supposed to do that isn't it. Well Still nothing happens when I login it still sits in the corner and nothing about the windows have changed.

---

### Post by TheRingmaster on 2006-12-15
> **Cikrum said:**
> Hello,
I believe this is the problem. When i press Ctrl-Alt-Backspace all of my open windows close and it gives me a black screen ie. terminal I believe and once I wait a few seconds it returns me to the login screen. I Have no idea what the problem is, Although it might be my resolution. Any Ideas??
Thx,
Cikrum
Edit--Stupid me its supposed to do that isn't it. Well Still nothing happens when I login it still sits in the corner and nothing about the windows have changed.
If you have said what I have done in the 21st post, you should see a red diamond in the corner by the clock. Right-click that and change the window manager to beryl. and yes it is supposed to go blank for a while if you do ctrl-alt-backspace

---

### Post by Cikrum on 2006-12-17
> **TheRingmaster said:**
> If you have said what I have done in the 21st post, you should see a red diamond in the corner by the clock. Right-click that and change the window manager to beryl. 
When I click the manager and choose the beryl manager stilll nothing happens it still doesn't change the windows or add any effects. Could this possibilly be a compatibility issue. I have the lastest Nvidia drivers, but is there anything else.
Thx
Cikrum

---

### Post by TheRingmaster on 2006-12-17
how did you even install and set it up. Is there a guide that you went by? You might want to go through that again.

ps. You may want to post your xorg.conf file here maybe someone more knowledgeable than myself can see a problem.

---

### Post by hikaricore on 2006-12-17
Ok let me verify the EXACT steps you are taking here:

First you **right click** on the _Beryl icon_.

Then you move your mouse down to the **fourth line of the menu** which is labeled:  "**Select Window Manager**"

Then you move your mouse slightly to the right (or possibly left) into the _submenu_ that opens.  There are_ two options_ here, **BERYL** and metacity.  And you're clicking **BERYL** and nothing is happening?

-

You may want to check to see (sorry you may have done this and I missed it, didn't read the first page) if your video card is running with direct rendering enabled.  From a terminal window you would type: *glxinfo | grep rendering*

---

### Post by Voltzz on 2006-12-17
Hi, I have somewhat the same problem (hikaircore, yes I do that but beryl does not get selected [it flickers windows a bit but nothing gets selected in the end])
I'm using ATI instead of Nvidia by the way.

I went by the official beryl wiki guide.

---

### Post by d3v1ant_0n3 on 2006-12-17
First step for trouble shooting: What happens if you have a session without beryl or beryl-manager running, and start it from the terminal using ```
beryl-manager
```

What output do you get from the terminal?

---

### Post by Voltzz on 2006-12-17
voltzz@Aurora:~$ beryl-manager
voltzz@Aurora:~$

It doesn't display anything, yet the red gem displays. (Beryl is not selected as windows manager)

---

### Post by Voltzz on 2006-12-17
I pressed "Beryl Settings Manager" by rightclicking and this appeared in the terminal

** ERROR **: no d_ for a_active_plugins
aborting...

---

