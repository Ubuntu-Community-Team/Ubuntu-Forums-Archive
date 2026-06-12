---
title: "Help:compiz and desktop cube problem"
date: 2008-04-22
forum: General Help
---

### Post by nelsyeung on 2008-04-22
I have been really stupid and used this post [http://ubuntuforums.org/showthread.php?t=601310]("http://ubuntuforums.org/showthread.php?t=601310")to install emerald, the post was really good and works, but i realize that "The guide is based on Kubuntu"....and im using ubuntu.  Then I realize that my desktop cube doesn't work anymore because it only shows 2 workspace or desktop, on a flat panel instead of a cube.

I used this command: "sudo gconf-editor" to check if the hsize value is 4.
the gconf editor came up and i went on this "apps >> compiz >> general >> screen0 >> options" the hsize value is 4, but it also says in the key doc "This key has no schema", also hsize is the only option there whereas before I have a whole list of options.

Is there anyway to fix this? Please help me, im abit new to linux.
Post any questions that you need to ask me.

---

### Post by Zorael on 2008-04-22
As far as Compiz is concerned, the difference between Kubuntu and Ubuntu is negligible. :>

You shouldn't need to edit any gconfs to get the number of desktops you want.

Do you have CCSM installed (package name **compizconfig-settings-manager**)? Get it through Synaptics or via a terminal.
```
$ sudo aptitude install compizconfig-settings-manager
```

You should get an entry in your Applications menu; 'Advanced Desktop Effects Settings'. Or you could just hit Alt+F2 and run **ccsm**.

Then go to General Options, Desktop Size. Set horizontal virtual size to 4, vertical size to 1 and number of desktops to 1.

It should take effect immediately. (Provided Compiz is running.)

---

### Post by nelsyeung on 2008-04-22
wow thanks **Zorael**.  Everything works now. :)

---

### Post by Garf on 2008-04-24
Mine is not working...

In my screen shot, you will see that I have set Horizontal desktops to 4... I can't edit the "Number of Desktops" option...

Also in the bottom left of the screen you will see that it is only showing 2 desktops.

Edit, probably should have posted a link to the image :)

[http://agsd.com.au/snapshot1.png](http://agsd.com.au/snapshot1.png)

---

### Post by Zorael on 2008-04-24
Is Compiz running to begin with? Open up a terminal and enter this.
```
$ compiz --replace --ignore-desktop-hints &
```

And if you have settings that mysteriously won't stay the way you set them, try exporting your profile under preferences, set backend to flat-file and then import your profile again.

I'm not sure when you're actually supposed to use Number of Desktops, so just ignore it for the time being. Horizontal virtual size to the sides you want on your paper/triangle/cube/etc, vertical size to 1.

---

### Post by Garf on 2008-04-24
Well it's telling me that:

```
Checking for Xgl: gareth@gareth-kubuntu:~$ not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin
```

Now I think why it's saying that Xgl is not isntalled, is because after I restarted the computer for the first time with Compiz running, all I could get for a resolution was 640 x 480.... So it had screwed my xorg.conf..

SO I had to do dpkg-reconfigure xserver-xorg (or something like that) to get my resolutions back... so maybe that is telling it that xgl is not installed..

Either way, it's been incredibly frustrating... this is supposed to be an LTS release (I know not for kubuntu, but still)... I never had any of these issues when using straight ubuntu... 

Anyway I I did aptitude search for xgl and got the following...

```
p   python-wxglade                  - GUI designer written in Python with wxPyth
pi  xserver-xgl                     - GL-based X server
```

I then tried to install xserver-xgl, still says 

```
Checking for Xgl: not present.
```

---

