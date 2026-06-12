---
title: "inkview"
date: 2022-02-12
forum: General Help
---

### Post by grey1beard on 2022-02-12
A search for an svg viewer often suggests inkview which "is packaged with  inkscape". Described as a standalone viewer, it sounds like what I'm looking for, but cannot find it.
I've checked my usr/bin files but no sign there.
I've also visited inkscape.org pages but with no result.
Can someone point me to a source, if I need to download it, or terminal code to run it, if it's hidden away from my prying eyes !
Regards
John

---

### Post by #&amp;thj^% on 2022-02-12
```
apt search inkscape
```
Link: [https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/inkscape_0.92.5-1ubuntu1_amd64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/inkscape_0.92.5-1ubuntu1_amd64.deb.html)
Also See Screenshot

---

### Post by grey1beard on 2022-02-12
Thanks 1fallen, but I'm no further forward.

apt search inkscape doesn't find anything, even though the link you gave shows it as a /usr/bin/inkview file in Inkscape 0.92.5-1.

I'm running 1.1.2, so perhaps it's been dropped ?
John

---

### Post by Bashing-om on 2022-02-12
grey1beard; Well

For focal - 20.04
```

apt show inkscape

```
shows as:
> 
Version: 0.92.5-1ubuntu1.1
//
 APT-Sources: [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) focal-updates/universe amd64 Packages

to be in the universe repo.

Do you have the universe repo enabled ?

[INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by grey1beard on 2022-02-12
Love the 'not so yes' !:P

However, it does seem that I have it -

[I]$ sudo add-apt-repository universe
'universe' distribution component is already enabled for all sources[/I]

John

---

### Post by Bashing-om on 2022-02-12
grey1beard; Well ! Not !

What release are we working with ?  -  I see what we can find from the changelog.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by grey1beard on 2022-02-12
Do I need to install ***Flatpak*** ?

---

### Post by grey1beard on 2022-02-12
I'm running 1.1.2

---

### Post by Bashing-om on 2022-02-12
grey1beard'
> 
Do I need to install Flatpak ?


No, inkscape in is the software repository. The question is - why you do not see it.

Please show us what release you are running:
show us:
```

lsb_release -a

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by grey1beard on 2022-02-12
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal

---

### Post by Bashing-om on 2022-02-12
grey1beard; Hummm ---

Sorry for the delay in responding - life gets in the way.

However - does not make sense as I too am on 20.04.3
and I get returns:
> 
sysop@2004x-c:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal

//
sysop@2004x-c:~$ apt list inkscape
Listing... Done
inkscape/focal-updates 0.92.5-1ubuntu1.1 amd64
inkscape/focal-updates 0.92.5-1ubuntu1.1 i386
sysop@2004x-c:~$


Let's poke at this a bit and see if something bites back:
what returns:
```

cat -n /etc/apt/sources.list
sudo apt update
sudo apt upgrade

```

[INDENT]a hunt'n we will go[/INDENT]

---

### Post by grey1beard on 2022-02-13
I've forgotten how to insert code result as a small package - do I wrap quotes around it ?(last icon at top of the Quick Reply window ?)

---

### Post by grey1beard on 2022-02-13
Tried html, but that doesn't seem right.

EDIT Off to bed, will  continue tomorrow.
John

---

### Post by Bashing-om on 2022-02-13
grey1beard -
> 
I've forgotten how to insert code result as a small package -


See:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]another bit to try and help
[/INDENT]

---

### Post by grey1beard on 2022-02-13
I've repeated the code, so the result is a little more compact this morning, but I hope it's helpful.

John

```
$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1)]/ focal main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
     6	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
    11	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ focal universe
    17	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
    19	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
    27	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
    29	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
    37	# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
    38	
    39	## Uncomment the following two lines to add software from Canonical's
    40	## 'partner' repository.
    41	## This software is not part of Ubuntu, but is offered by Canonical and the
    42	## respective vendors as a service to Ubuntu users.
    43	# deb http://archive.canonical.com/ubuntu focal partner
    44	# deb-src http://archive.canonical.com/ubuntu focal partner
    45	
    46	deb http://security.ubuntu.com/ubuntu focal-security main restricted
    47	# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
    48	deb http://security.ubuntu.com/ubuntu focal-security universe
    49	# deb-src http://security.ubuntu.com/ubuntu focal-security universe
    50	deb http://security.ubuntu.com/ubuntu focal-security multiverse
    51	# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse
    52	
    53	# This system was installed using small removable media
    54	# (e.g. netinst, live or single CD). The matching "deb cdrom"
    55	# entries were disabled at the end of the installation process.
    56	# For information about how to configure apt package sources,
    57	# see the sources.list(5) manual.
john@john-HP-ProDesk-600-G1-SFF:~$ sudo apt update
[sudo] password for john: 
Sorry, try again.
[sudo] password for john: 
Hit:1 http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease            
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Get:6 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40.6 kB]
Get:7 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.3 kB]
Get:8 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Err:9 http://dl.google.com/linux/earth/deb stable InRelease                    
  Temporary failure resolving 'dl.google.com'
Fetched 223 kB in 30s (7,426 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/InRelease  Temporary failure resolving 'dl.google.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by dragonfly41 on 2022-02-13
I would cut to the chase and install Synaptic Package Manager to search for Inkscape.

sudo apt install synaptic

But that apart you might like to explore [Boxy-SVG]("https://boxy-svg.com/").

Note: select FREE version from Snap tab. But still try to get Inkscape since it is the gold standard.

---

### Post by grey1beard on 2022-02-13
Are we at cross purposes here ?
I've got inkscape 1.1.2, and I'm trying to get **inkview** to use to view all the .svg files I have created.
John

---

### Post by dragonfly41 on 2022-02-13
I see. Can you [use command line]("https://www.mankier.com/1/inkview") to view .svg files?

"[COLOR=#000000]or terminal code to run it" from post#1.

This example works for me.

[/COLOR][FONT=monospace][COLOR=#000000]```
inkview /usr/share/inkscape/examples/tiger.svgz
```

[P.S.] I should add a caveat here.

I ran the command ```
sudo locate inkview
``` to find inkview location.

I see that I have several locations.

/usr/bin/inkview
/snap/inkscape/9711/bin/inkview
/snap/inkscape/9866/bin/inkview
and others in different languages: de, es, fr, hr, hu.

suggesting to me that I had an earlier installation of inkscape;inkview followed by snap version.


[/COLOR]
[/FONT]

---

### Post by grey1beard on 2022-02-13
*sudo locate inkview*
 command *locate* not found
!!

/usr/bin/inkview
/snap/inkscape/9711/bin/inkview
/snap/inkscape/9866/bin/inkview

no results.  9711 nor 9866 have a bin folder.

---

### Post by dragonfly41 on 2022-02-13
I just experienced a one hour electricity blackout.

The snap id's are probably unique to my installation.

Try first .. **snap --help**

You should see command list

Now try [B]snap list
[/B]
In output list I have 
[FONT=monospace][COLOR=#000000]
[B]boxy-svg 3.77.0 81     latest/stable    jarek-foksa 
[/B][/COLOR][/FONT][FONT=monospace]**[COLOR=#000000]inkscape 1.1.2-b8e25be833-2022-02-05  9866   latest/stable    inkscape[/COLOR][COLOR=#18B218]&#10003;[/COLOR]**[COLOR=#000000]              -[/COLOR]
[/FONT]
[FONT=monospace]
[/FONT]Probably boxy-svg uses inkview. Certainly inkscape.

Then I have an earlier installation of inkscape (predating snap version)

[FONT=monospace][B][COLOR=#000000]which inkscape[/COLOR]
/usr/bin/inkscape[/B]

[/FONT]That explains my three hits.

It is possible that **sudo locate inkview** does not locate **inkview** on first use.
Try running **sudo update** and wait some minutes for file system to be indexed.
Then try **sudo locate inkview** again
If not found then it is not installed.
[FONT=monospace]
[/FONT]

---

### Post by grey1beard on 2022-02-13
I have the same inkscape - * 1.1.2-b8e25be833-2022-02-05  9866   latest/stable    inkscape&#10003;* 
> 
Then I have an earlier installation of inkscape (predating snap version)
Are you saying that you have two versions of inkscape installed ?

---

### Post by deadflowr on 2022-02-13
> Are you saying that you have two versions of inkscape installed ?

You can install the snap version and the apt version of packages at the same time.

---

### Post by dragonfly41 on 2022-02-13
[COLOR=#000000][INDENT]"Are you saying that you have two versions of inkscape installed ?"

Yes.  The Inkscape package which I installed through Synaptic Package Manager (see earlier suggestion) is quite separate from the snap installation. And I'm guessing that Boxy-SVG which is an SVG editor also uses inkview. This is one of the downsides of snap apps .. resources can be duplicated. Your best bet is to use Synaptic Package Manager. Why do you choose not to follow that advice?[/INDENT]
[/COLOR]

---

### Post by grey1beard on 2022-02-13
I've just gone to the Inkscape website and searched for Inkview and No Results showed up !
So am I on a road to nowhere ?

---

### Post by grey1beard on 2022-02-13
I don't choose not to follow advice. This is why I have always come here, for the help so freely given by everyone.
I have just gone back over the thread, and spotted your suggestion, which I missed. My bad.
I shall now do that, and see what it produces.
Please note my latest post that the inkscape site itself doesn't mention inkview, so I wait with interest.
Regards
John

---

### Post by grey1beard on 2022-02-13
Deadflower - Thanks for the info. More learning for this old brain !

---

### Post by grey1beard on 2022-02-13
Dragonfly41
I hesitate to install a second version, probably a combination of my advanced years and the worry about all the .svg files that I have produced over the years, and currently working with.
When I first joined the Ubuntu community, I took to heart the advice not to do anything that you didn't understand, nor were uncomfortable with.
Although I've managed to get myself in all sorts of knots, my experience has been that with the patient help of everyone here, it all gets sorted, and life goes on.

If I have two instances of Inkspace, will I have any difficulty of moving files between the two ?

---

### Post by dragonfly41 on 2022-02-13
Caution is not a bad thing. But nothing ventured, nothing gained.
Really svg files can be tamed.

You can have two versions of Inkscape.  The reason you cannot download inkview is that it is installed as a binary at time of installing inkscape. I have other apps which install different binaries. For example I use a small tool Actiona for desktop automation and it has a binary actexec expressly used for running scripts without GUI. Inkview seems to be the same. A viewer only sans GUI. See earlier link to using inkview at command line.

Do try also Boxy-SVG as suggested. There is a web demo which does not require installation.

[P.S.] [In case you missed this earlier link.]("https://www.mankier.com/1/inkview")

[P.P.S.] It seems to be true that inkview does not appear in any search on Inkscape web site or forum which is strange.


================================================

Conclusion

If you have many SVG files which you intend to preview in a slideshow there are other ways of achieving that. I would just use Markdown with SVG filepaths embedded and then use Pandoc > revealjs to create an HTML slide show with embedded SVG objects. If you need advice on that approach I can add more notes .. tomorrow.

---

### Post by grey1beard on 2022-02-13
My first inclination is to follow your suggestion of installing a second instance of Inkscape.

(I admit I've never been comfortable with Snap, which seems to be oddly aggressive compared with what I was used to, - forgotten now, but it was probably synaptic.
All in the mind. Must keep taking the tablets.)

---

### Post by dragonfly41 on 2022-02-13
Snap is .. not favoured by some .. but keeps everything in containers.

Reading your post#17
[COLOR=#000000]"[/COLOR]   I'm trying to get inkview to use to view all the .svg files I have created.   "
leads me to the approach to use Markdown with embedded SVG.

How many SVG files do you hope to view?

Example: read Vector Graphics in [this blog]("https://jaantollander.com/post/scientific-writing-with-markdown/"). There are many more such articles.

---

### Post by grey1beard on 2022-02-13
Might be about ten. 
I'm a fan maker, designing frames for them.
 I probably get through up to ten iterations of a design before I get the dimensions right, saving each, but forgetting what I called the 2nd/3rd version when I want to go back and start again.
So having a viewer, even that shows only a thumbnail sized image, would short cut the process of getting the one I want.
Using the normal file manager in ubuntu doesn't give me any image, so that's a slow process.
I've just loaded my second instance of inkscape, but each time I try to use terminal to get help/version/etc or any info, it tells me that it *Failed to load module "canberra-gtk-module"*, so a bit puzzled as to what to do next.
When I get to having it all running, is it possible to have a short cut to load it as a gui ?
EDIT tried to use*  sudo apt-get canberra-gtk-module* and terminal reported invalid operation.

Edit2 I've read through the Markdown link, and I confess most of it is well over my head. 
The last paragraph > Vector Graphics

Markdown allows inserting vector graphics with the standard syntax.

![](<filename>.svg)

Using vector graphics when creating PDFs requires Inkscape.
sends me back to square one, as far as I can see.

---

### Post by grey1beard on 2022-02-13
I've now installed mlocate, and lo and behold, I now find inkview in the multiple places that you have pointed me to.
All I need to do now is try it out.
Many thanks for your help and patience.
Regards to all,
John
PS I'll post this as solved when I have used it !!

---

### Post by grey1beard on 2022-02-13
On the Man pages for inkview, it says

> You can also launch Inkview without any command-line arguments, which will bring up a file chooser that allows to select files and folders via a graphical user interface.

 but with no 'how to'.

I've tried in Terminal **inkview**, but it suggested options, so I tried **inkview -f** and got *Failed to load module "canberra-gtk-module"*

So I tried **locate -i canberra-gtk-module**, and got 

```
locate -i canberra-gtk-module
/snap/gimp/380/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gimp/380/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/snap/gimp/380/usr/share/doc/libcanberra-gtk-module
/snap/gimp/380/usr/share/doc/libcanberra-gtk-module/changelog.Debian.gz
/snap/gimp/380/usr/share/doc/libcanberra-gtk-module/copyright
/snap/gimp/383/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gimp/383/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/snap/gimp/383/usr/share/doc/libcanberra-gtk-module
/snap/gimp/383/usr/share/doc/libcanberra-gtk-module/changelog.Debian.gz
/snap/gimp/383/usr/share/doc/libcanberra-gtk-module/copyright
/snap/gnome-3-28-1804/145/usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/gnome-3-28-1804/161/usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/gnome-3-34-1804/72/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gnome-3-34-1804/72/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/gnome-3-34-1804/77/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gnome-3-34-1804/77/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/gnome-3-38-2004/87/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gnome-3-38-2004/87/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/gnome-3-38-2004/99/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/gnome-3-38-2004/99/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
/snap/inkscape/9711/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/inkscape/9711/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
/snap/inkscape/9711/usr/share/doc/libcanberra-gtk-module
/snap/inkscape/9711/usr/share/doc/libcanberra-gtk-module/changelog.Debian.gz
/snap/inkscape/9711/usr/share/doc/libcanberra-gtk-module/copyright
/snap/inkscape/9866/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop
/snap/inkscape/9866/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
/snap/inkscape/9866/usr/share/doc/libcanberra-gtk-module
/snap/inkscape/9866/usr/share/doc/libcanberra-gtk-module/changelog.Debian.gz
/snap/inkscape/9866/usr/share/doc/libcanberra-gtk-module/copyright
/usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libcanberra-gtk-module.so
``` 

So I seem to have some headway, but not got a result yet.

---

### Post by grey1beard on 2022-02-13
I have now run **sudo apt-get install libcanberra-gtk-module** and no longer get the error message.
If I now run inkview Desktop/trefoil.svg it opens in a full screen, so some progress.
The screen seems to be fixed in size at the moment, and as I work with minimal line width, nothing is visible, unless I increase it to a couple of mms.
However, progress of a sort. Try again tomorrow.

---

### Post by dragonfly41 on 2022-02-14
In post #33 you write this about man inkview .. &#8220;but with no 'how to'. &#8221;

Clearly you have missed links in earlier posts.

Here it is again .. from post #28

> [P.S.] [In case you missed this earlier link.]("https://www.mankier.com/1/inkview")


Now we are clearer that

you design fan images in svg
you have only ten images at a time to preview but you might have ten or so variants of each.
you are not comfortable with markdown (but in fact markdown idea was to only embed final svg files for an svg album, before we learned that you design fans)
you would like to &#8220;tweak&#8221; your svg designs and preview results

Inkscape is an essential tool and you have this working.

Assumption is that you prefer to tweak designs using a GUI rather than in svg code directly. 

Returning to inkview (which is your choice) I noted that you do not have this 

/usr/lib/gnome-settings-daemon-3.0/gtk-modules/canberra-gtk-module.desktop


But you have now installed it.


In my Synaptic I see

ink-generator
Inkscape extension to automatically generate files from a template

inkscape-tutorials
vector-based drawing program - tutorials


...


To return to my earlier idea to try Boxy-SVG (as supplement to Inkscape and Inkview)

[https://boxy-svg.com/](https://boxy-svg.com/)

Start by clicking on LAUNCH APP  which opens in your browser. No installation required to test it.

File > Open from disk > ~/Desktop/trefoil.svg

Click on Elements tab at bottom of Boxy-SVG screen.

Click on tab at left to expand SVG tree.

You can now edit the elements of trefoil.svg

You can save as trefoil-version1.svg

If you create a User Account there are built in Blogs, Tutorials and Ideas to explore.

[https://boxy-svg.com/tutorials/J_Q4YLoW45A/selecting-objects](https://boxy-svg.com/tutorials/J_Q4YLoW45A/selecting-objects)

You can also install your local snap version of Boxy-SVG on Ubuntu.
Linux installations are free.

If you get around to publishing embedded SVG designs in documents that is another subject for another day.

---

### Post by grey1beard on 2022-02-14
Thank you dragonfly41 for your thoughtful response.

Late last night I discovered how I needed to modify all my saved designs in order to have them visible in inkview. This would involve 'thickening' all the paths in the design, then saving them.

However, until I can move on a little further with my use of this software, it doesn't seem to offer me any advantage over the current method I use of guessing from a list of 'recent files', and then opening it in inkscape.

What I'm looking for to be clear, is a viewer that has an album of thumbnails of svg files. 

I now realise that I would have the same problem with any viewer along the lines(forgive the pun), that on the scale of the drawing, the lines would be invisible in a thumbnail.

I shall follow your suggestion of trying boxy-svg , and see if that gets me past this problem.
Thanks again for your help, and Happy Valentine's Day.
John

---

### Post by dragonfly41 on 2022-02-14
> [COLOR=#000000]What I'm looking for to be clear, is a viewer that has an album of thumbnails of svg files.[/COLOR]

Try Gnome gThumb first for an album of thumbnail svg files. There are other viewers to try.

---

### Post by #&amp;thj^% on 2022-02-14
> **dragonfly41 said:**
> Try Gnome gThumb first for an album of thumbnail svg files. There are other viewers to try.

Good posts dragonfly41 ;)
Some other suggestions if I may: [https://itsfoss.com/image-viewers-linux/](https://itsfoss.com/image-viewers-linux/)
Grain of salt not all fits your needs.

---

### Post by grey1beard on 2022-02-14
Thanks 1fallen. I've had a quick look, but I suspect that, as mentioned in #36, 
> I now realise that I would have the same problem with any viewer along the lines(forgive the pun), that on the scale of the drawing, the lines would be invisible in a thumbnail.
so I may be on a fool's errand.

Perhaps my better move would be to think more carefully about how I name my files, and delete far more.
 Bit of a jackdaw, I suppose !](*,)

---

### Post by #&amp;thj^% on 2022-02-14
> **grey1beard said:**
> 
 Bit of a jackdaw, I suppose !](*,)
Been there a time or two myself. ;)
Best Regards

---

### Post by dragonfly41 on 2022-02-14
Another gameplan is to approach SVG editing as a coding exercise.

[http://snapsvg.io/](http://snapsvg.io/)

Just dive into the svg code (which is xml format).
I have also used XMLCopyEditor to edit svg elements.

But there is a learning curve.

---

### Post by Holger_Gehrke on 2022-02-14
You might want to give geeqie a look. It's a general image viewer  / organizer which does handle a lot of formats including SVG and gnuzip compressed svg (SVGZ). The way I have it set up it has a directory tree and a panel with preview images on the left side of the window and the rest is a full view of the currently selected image. It does tend to choke on very complex SVG drawings, which can lead to the program becoming unresponsive for several minutes (don't try to open the /usr/share/inkscape/examples directory in geeqie, it has a lot of those ...)

Holger

---

### Post by grey1beard on 2022-02-14
Thanks Holger.
Geequi looks a definite possibility. 
Having got to grips with the preferences, I can now view some of my svg files OK.

However, nearly all are saved with a 0.1 px wide line( I'm using them as cutting files for my Glowforge laser) and are therefore invisible in the window.
Perhaps I need to save them with a wider line in future, but definitely looks promising.
John

---

