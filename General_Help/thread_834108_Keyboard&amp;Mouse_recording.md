---
title: "Keyboard&amp;Mouse recording?"
date: 2008-06-19
forum: General Help
---

### Post by pnhsp on 2008-06-19
Hi, I need Mouse and Keyboard Recording and Playback program for Ubuntu or other linux sistems.

I found 2 Programs.
XNEE, XMACRO .
Im beginner on the linux.

How to using XNEE or XMACRO?

Im using Easy macro recorder on the MS XP os.
Now, Im using Ubuntu, No macro recorder programs ,Please help me!!!

Easy, basic with gui windows macro recorder programs on the WindowsXP 
Can you help me installation and Using execution thisprograms.

---

### Post by aresgodofwar30 on 2008-06-19
Can you elaborate more on what you want to accomplish? I know of screencasting, which is not the same as macro recording, but it records your desktop. 

Depending on your needs, a shell script may be an easier way to go.

---

### Post by pnhsp on 2008-06-19
Hi, Im sorry for my english.

I want to record basic  mouse keyboard all events on the linux (ubuntu ) desktop and playback all events.

Example

-Open the terminal (console screen ) writing pppoe-startand enter , go

Mouse pointer go the Opera web browser and clicking download file. Ok. I 'm using macro recorder program on the windows, Easy, basic using. Very easy.

Now Im using linux not a easy program, ALL  have to Command line parameters, Codes.

Please Can you watcing the video 

[http://www.youtube.com/v/JudsrlumDEc](http://www.youtube.com/v/JudsrlumDEc)

Do you understand me? :confused:

---

### Post by pedro_orange on 2008-06-19
What you wanna do is work out what commands do the things you want to do.

Eg. to open Opera you just type in "opera" in terminal.

Once you've got your commands, set them up as scripts and run as and when needed.

---

### Post by pnhsp on 2008-06-19
I dont know writting to script, codes ,bash.

I do install XNEE, but Im not using, not working application.
So, Your lend assistance for GNU XNEE program  installation and Usage???

[http://www.gnu.org/software/xnee/](http://www.gnu.org/software/xnee/)
How to working xnee application?
What are the codes, start XNEE macro recorder?

---

### Post by aouie on 2008-07-23
Installing latest xnee.
Download the latest xnee from [the Xnee site http://savannah.gnu.org/projects/xnee/]("http://savannah.gnu.org/projects/xnee/").
Extract the archive to some folder.
Go over to the folder and then type:
```
./configure --enable-gnome-applet --prefix=/usr

```
Unless you had all the necessary files in place you will not succeed in the previous step.
Try installing from synaptic: libpanel-applet2-dev, build-essential, libxtst-dev, and libgtk2.0-dev (this will also install several dependencies).
Now try the configure step again and it should succeed.
Then type:
```
make
sudo make install
sudo gedit /etc/X11/xorg.conf

```
Add the following line in the module section
```
Load "record"

```
Restart X. (If you don't know how, then simply restart the computer (or logout (and just to be sure CTRL+ALT+BACKSPACE) and log back in)).
You could learn to use GNEE, but I stuck to CNEE.

I created two bash scripts (which you can put in /usr/local/bin if you don't know how else to set it up) (Make them executables. (In Nautilus file manager right click on file then set to executable on the permissions tab.)
Script 1 is MacRec
```
sleep 0.3s
cnee --record -o /tmp/cnee_$1.xns --events-to-record 10000 --keyboard  --stop-key Shift_R

```

Script 2 is MacPlay
```
sleep 0.3s
cnee --replay --keyboard --file /tmp/cnee_$1.xns --stop-key Shift_R -sp 10

```

On any terminal (command prompt) type MacRec 1 (or any other value "Val" to create a tmp macro file /tmp/cnee_Val.xns).
Hit the right shift key to stop recording the events.

MacPlay 1 (or whatever "Val" you used) should play back the file.

You should just have to add --mouse to the cnee arguments to record and play back mouse events, but I didn't test that.

Now setup your keyboard shortcuts for your desktop (On XFCE it is under Settings->Settings Manager->Keyboard, for gnome it is probably under System->Preferences->Keyboard), I setup shortcuts for the commands "MacRec 1", "MacPlay 1", "MacRec 2" and "MacPlay 2".

Either look up the documentation on the site or "man cnee" to check what other options you may find useful in cnee.

Sincerely,
Aouie

---

