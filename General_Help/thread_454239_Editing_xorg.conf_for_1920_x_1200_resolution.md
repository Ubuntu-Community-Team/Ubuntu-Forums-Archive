---
title: "Editing xorg.conf for 1920 x 1200 resolution"
date: 2007-05-25
forum: General Help
---

### Post by erugalatha on 2007-05-25
Hi,

I've been fighting with Feisty Fawn and trynig to get my native resolution working (1920 x1200) on my ATI x1400 graphics card.

So far I've enabled the restricted drivers successfully but when I try to change the resolution I only get the option of 1024 x 768.  

What do I do next to be able to get 1920 x1200?

---

### Post by mwells on 2007-05-25
Hi there,

Congratulations on getting Feisty up and running.

THe issue of the resolution is a common one, and unfortunately at the moment involves the manual editting of the xorg.conf file.

first thing though is to back this file up, as any mistakes in its editing can leave you with a daunting black screen when you restart your laptop!

so from a terminal type (you will be prompted for your root password)

```

  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk

```

We now have a backup created which we can restore if everything goes pear shaped!

now open the file in your text editorof choice (gedit if your on gnome, kate if on KDE) using the below code

```

sudo gedit /etc/X11/xorg.conf

```

The file should now open, you should then scroll down to the section titled "Section Screen". Within this section you should note a number of different resolutions listed. You need to add your desired resolution to each one of these lines following the same format of those currently there. You can then restart your computer and the changes should be reapplied

Just be carefull when you are making these edits, and check your typing as you go! other than that there is no real difficulty to it!!

NOTE: if you are confronted with a black screen on restart simply login via the terminal and tyle the following

```

sudo rm /etc/X11/xorg.conf

sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf

```

This will reinstate your previous version and you should then be able to restart with no problems

Hope that helps!

/Matt

---

### Post by erugalatha on 2007-05-25
Thanks a lot ... I've already had the black screen when I booted feisty for the first time after install ... it took me days to figure out how to get to a command line from there. :)

I'll try your suggestion ... thanks again.

---

### Post by gustavoberman on 2007-05-25
or, if you don't understand xorg.conf lines just use : sudo dpkg-reconfigure xserver-xorg
and follow intructions

---

### Post by erugalatha on 2007-05-25
I tried that too - it asked me stuff about reconfiguring screen depth and about PS/2 input devices etc.  Way above an average users capabilities IMHO. :)

I chose vesa in that reconfiguration and that's how I got the X server to start graphically.  I don't think it's actually configured correctly for my x1400 graphics card at all as it just shows cra*py 1024x768 resolution even though the restricted driver is enabled.

I want to get beryl working too but I'm taking it a step at a time - just want to get native resolution of 1920 x1200 for now.

---

### Post by grogger13 on 2007-05-25
I have your exact card with the same resolution(Dell E1705) i used the envy script to install the ATI proprietary drivers.

search "envy" in synaptic

i use beryl too and I know you need xgl + beryl to get it working properly

---

### Post by erugalatha on 2007-05-25
to find this envy script do I need to add a repository?  I searched in synaptic but nothing is returned for "envy".

---

### Post by erugalatha on 2007-05-25
ok I installed envy from a .deb package and then installed the ATI driver using envy but I still only have 1024 x 768 resolution.

There's no reference to my ATI x1400 graphics card in xorg.conf file.

---

### Post by Chuq on 2007-05-29
Very odd.. I've got a Geforce 7100 GS and a Dell 24" LCD and having issues getting it to work at full resolution.

I've tried manually editing /etc/X11/xorg.conf, I've tried the "sudo dpkg-reconfigure xserver-org" method, both times after I restart and go into System > Preferences > Screen resolution, the same 3 options are there - 1024x768, 800x600, 640x480.

The res I'm trying to get is 1920x1200.

Am I supposed to be looking somewhere else?

Any other ideas?

---

### Post by Chuq on 2007-05-29
Naturally, as soon as I post the message, I find the fix :P

I re-enabled the Nvidia restricted driver and I get a choice of about 20 resolutions in the 'screen resolution' dialog box!

Oh well, at least this question and answer may help someone else with the same problem ...

---

### Post by Memory.Dump on 2007-05-29
honestly try 
```
sudo dpkg-reconfigure xserver-xorg

```

I did it and I didn't understand most of what it was saying, basiclly if you don't know what it is you can leave it with what info is already there or leave it blank and it will set defaults so you don't need to know just aggree then near the end you can select your resolutions to add worked great for me

---

### Post by erugalatha on 2007-05-30
I've been messing around with this for over a week now but finally got XGL/BERYL native resolution etc. up and running the way I want.

To get your native resolution working on Feisty correctly go here and follow the steps:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

For anyone who's interested (and has the same machine) this is all working an Alienware m550 Area 51m with an ATI Mobility Radeon x1400 and 1GB of RAM.  

Beryl looks so sweet on Alienware! :D

---

