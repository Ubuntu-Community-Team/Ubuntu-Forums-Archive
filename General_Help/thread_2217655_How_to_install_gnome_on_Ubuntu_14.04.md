---
title: "How to install gnome on Ubuntu 14.04"
date: 2014-04-18
forum: General Help
---

### Post by offir on 2014-04-18
I do not know exactly to which Forum
This issue belongs to
Or this forum or forum Installation and Upgrading



I installed Ubuntu 14.04 on a computer
New computer

After installation I installed it through software manager
gnome classic

I click log out
Then enters through the interface of gnome

It works
But I do reboot it does not work anymore
There is no way to get to Desktop other than reformatting

I have already made four installations



How do I solve it
Put gnome instead of unity

---

### Post by kc1di on 2014-04-18
Hello offir,

When you say it no longer works , can you explain what exactly is happening.  Do you get to the login screen?  or is it a black screen? 
if the login screen can you login to unity and not gnome , We need a little more information to be able to help.

Some particulars about your machine would also be helpful  what video card is it using?  

If you want gnome desktop shell why not download the ubuntu-gnome release.  It may save you some trouble.  It's very rare you would have to reformat your drive.

Give us some more information so we can be of better help.

---

### Post by offir on 2014-04-18
I get a black screen which can not do anything 

Graphics card is integrated

ThinkCentre M57e (9439-CTO) i add 2 giga memory card {total of 3 giga}

---

### Post by offir on 2014-04-18
More details

Currently I'm using version 10.04
I skipped version 12.04
The graphical interface was uncomfortable

I have another computer with 12.04 on it I installed it the gnome {not mine}
It works

I want to do the same here

Both computers use compiz

I do not want the toolbar that on the side

---

### Post by mJayk on 2014-04-18
If you want gnome3 with ubuntu you should probably look at the gnome-ubuntu remix.

---

### Post by sdowney717 on 2014-04-18
I do it like this

sudo apt-get install gnome

during install tell it use lightdm when asked

reboot

click icon next to user login to select the gnomes

---

### Post by kc1di on 2014-04-18
Like others have said if you want gnome you should install ubuntu gnome .
was unity working ok after you originally installed it?
if so then your video card should be working and something changed when you tried to install gnome. 
in any event, if you don't want to re-install gnome re-mix then follow the steps on [this page ]("http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell")and and go to recovery mode. 
When you get there go to a terminal and type this command and copy the results here so we can see the video card your machine is using.

---

### Post by grahammechanical on 2014-04-18
If you are using Ubuntu+Unity 14.04 I would not recommend installing anything called Gnome Classic because that is a Gnome 3 shell extension. It would need Gnome 3 shell to be installed as well. To get Gnome 3 shell we can install Ubuntu Gnome and then Gnome Classic will work fine.

With Ubuntu+Unity we should install gnome-session-flashback. That will give us 2 extra options at login - Gnome Flashback (Compiz) and Gnome Flashback (Metacity). Both give the so called "Classic" look.

Using Gnome 3 shell and its extensions on Ubuntu is a bit of an experiment, in my opinion.  The Ubuntu Gnome developers work hard to give a good user experience with Gnome 3 shell. There are less likely to be problems with Ubuntu Gnome then with Ubuntu+Unity+Gnome 3 shell. Keep also in mind that Gnome 3 shell is also under continual development. 

Regards.

Edit; Ubuntu Gnome

[http://ubuntugnome.org/](http://ubuntugnome.org/)

---

### Post by offir on 2014-04-18
> If you want gnome3 with ubuntu you should probably look at the gnome-ubuntu remix. 

What is gnome-ubuntu remix ?




> I do it like this

sudo apt-get install gnome

during install tell it use lightdm when asked

reboot

click icon next to user login to select the gnomes 


what is lightdm ?





I used the version of Ubuntu gnome
Disk without installation

And the screen kept blinking until I turn off the computer maybe 10 minutes

---

### Post by offir on 2014-04-18
Now I'm after installation of ubuntu gnome
The computer asked me to eject the disc
I took the disk
Computer did reboot
And the system is up and I got a black screen
The screen flickered a few times until I got only a black screen







Update

After the second installation of gnome

Go in to gnome classic

Meanwhile it works



How do I gets rid of the top and bottom bar

---

### Post by sdowney717 on 2014-04-18
to get rid of the bottom bar, run gnome, not gnome classic.
I think you can get rid of the top bar in gnome classic.

If you use lightdm, your login is standard ubuntu look.
If you use gdm, your login has the gnome look.

So if you select gnome, your screen is black?
What happens if you select ubuntu?

---

### Post by offir on 2014-04-18
> So if you select gnome, your screen is black?
What happens if you select ubuntu? 

i have only one system installed

First time i had ubuntu unity
After I installed on it gnome
He stopped working What I got it just a black screen

The second time
I installed gnome
For some reason it did not work well
After the first reboot it got a black screen and that's it
You could not do anything


The third time I installed gnome again
This time it worked roughly
The screen flickered many times
Until he stopped
I did log out
Then log in after I chose gnome classic

Currently it works I have never encountered a problem
Besides that I want to remove the two toolbars up and down

---

