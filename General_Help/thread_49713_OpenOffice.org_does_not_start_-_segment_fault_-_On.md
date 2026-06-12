---
title: "OpenOffice.org does not start - segment fault - One possible FIX"
date: 2005-07-17
forum: General Help
---

### Post by ocumo on 2005-07-17
Ever since I installed [COLOR=DarkRed]Ubuntu Hoary[/COLOR] in this new Laptop, I had the following issue:

Summary of the problem:
**[COLOR=Indigo]OpenOffice.org v1.1.3 does not start up**. Error message in shell:Segment Fault.[/COLOR]
Machine: **HP Pavilion dv4000 Laptop**
Symptom: Starting OpenOffice.org from the menu (any of the OO apps) make the OO task bar appear with the hourglass for a few seconds and then disappears.

I started "Googleing" and found a thread in the ooo forum. A guy had the same problem, but with different machine. He fixed his problem in a way that did not help me.

So I after I fougth this problem for a while, I found a way to fix it, and wrote a howto for that. I am copying here the procedure, in the hope that it can help others, and in the hope that others, better informed and more experienced than me, can explain why this happens and if there is better fix than mine. I thank any constructive comments to this HOWTO.( And by the way, this is the original thread [http://www.oooforum.org/forum/viewtopic.phtml?t=21728](http://www.oooforum.org/forum/viewtopic.phtml?t=21728) , where you can see additional details on how I ended with this procedure).

[COLOR=Navy][SIZE=3]**_HOWTO Fix this: OpenOffice.org does not start in Ubuntu, on HP Pavilion dv4000 Laptop_**[/SIZE][/COLOR]

**1.- **Open a terminal shell as **root**.

You are going to edit your xorg.conf file, commenting a couple of lines, so be careful:

**2.- **At the **root** prompt, type the following two commands (enter at the end of each line)
```
cd  /etc/X11/
cp  xorg.conf  xorg.conf.original
```
The first line will change your directory, the second line will make a backup copy of the xorg.conf file, in case you want to easily restore everything to original.

**3.-** Enter the following command:
```
gedit  xorg.conf
```
This will open the xorg.conf file for edition.
[SIZE=1][color=darkblue](Note: this is assuming that you are running Gnome, so I use gedit. If you are running KDE, you should use kate instead of gedit, or then use whatever text editor you like).[/color][/SIZE]

**4.-** Look for the following line:
```
Load  "dri"
```
and type a **#** at the left to transform this line into a comment. It should look now like this:
```
# Load  "dri"
```
Note: it doesn't matter whether you left spaces or not between the # and the word *Load.* Anything to the right of the **#** will be considered a comment and hence **not** carried out during the boot up.

**5.- **Now, scroll down until you see a section with the title "Section DRI", which looks like this:
```
Section DRI
        Mode      0666
EndSection
```
Comment these three lines with **#**, like this:
```
# Section DRI
       #  Mode      0666
# EndSection
```
**6.- **So now, after you have commented the four lines related to the DRI module, **save** the file, and then **close** it.

**7.- **Shut down and restart your system. Openoffice.org **will** now work.
[color=darkblue]
**Rationale**[/color]

What I have done? (or what I *think* I have done...)

Ok, it took some work and trial and error to figure out, but now it is clear that the DRI (Direct Rendering Infrastructure) (see:  [http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)) and Oo.org v1.1.3 running in [COLOR=DarkRed]Ubuntu Hoary on a HP Pavilion dv4000[/COLOR] don't like each other. So, by commenting the lines that load the module DRI and set the permissions to 0666 (user, group and everybody else can read, write but not execute), what we are doing is preventing the system to use the features that this module offers. Reading the above link, and also this [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)   , one can see that the DRI module "allows direct access to graphics hardware under the X Window System" . Now, in which ways not having this feature will affect the rest of the system, that remains to be seen (please post if you know). So far, I have been testing all my programs and not noticed any abnormalities. Perhaps if I would install 3D games or stuff that uses hardware acceleration, I guess I might not get the best performance...

But one thing is for sure: According to Synaptic, if I choose to uninstall **xlibmesa-dri** (which seems to be the package that includes the module I am talking about), the packages **ubuntu-desktop** and **x-window-system-core** will also be removed, so those depend on the first. I don't think I want to uninstall my desktop, anyway, so commenting the lines as per my HOWTO is much safer, and if I find any trouble from that, I can always restore the original xorg.conf file.

If anybody find that this method is wrong, unnecessary, or harms any other important functionalities of the Operating System, **please post here your kind comments and suggestions, so we all can learn** from your wisdom.

I also don't know if the problem will exist as well with newer versions of OO.

Kind regards,

Ocumo

---

### Post by dollydoll on 2006-11-15
HI Thanks a lot!!
I am running Ubuntu 6.10 Edgy on a PC, and your how to did the job!
thanks again.

---

