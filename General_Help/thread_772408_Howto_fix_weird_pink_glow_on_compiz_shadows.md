---
title: "Howto fix weird pink glow on compiz shadows"
date: 2008-04-28
forum: General Help
---

### Post by ArchLinuxFan on 2008-04-28
So, after banging my head for weeks trying to fix the weird glowing pink & yellow borders / no shadow issue on Hardy and Nvidia 8xxx cards.. I came across a simple solution from a guy on the nvnews forum. 

It involves removing a badly linked .so file from the Nvidia driver and re-symlinking it to the X server core instead. Go figure.. ?

*Instructions : *

- Open a terminal window.

- Type: **sudo rm /usr/lib/xorg/modules/libwfb.so**

- Then type: **sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so**

- Restart X (either reboot or "Alt-Ctrl-Backspace")

Now you can enjoy Hardy in all its proper black drop-shadowy goodness. \\:D/

Let me know if this works for you - [read original discovery thread]("http://www.nvnews.net/vbulletin/showthread.php?t=109546&page=2")

---

### Post by FredB on 2008-04-28
Thanks for the info. Even if I don't have a 8xxx GPU, it could be useful to know.

---

### Post by Islington on 2008-04-28
nice! I saw this bug(?) pop up atleast twice on the forums.

---

### Post by ArchLinuxFan on 2008-04-28
For those worried about using the rm command, you can also substitute this for the second step to make a backup :
type: **sudo mv /usr/lib/xorg/modules/libwfb.so /usr/lib/xorg/modules/libwfb.so.bak**

---

### Post by Alehbye on 2008-04-28
I'm pretty new to Compiz as the system I just built was a Windows machine, but when I converted it this weekend and started using Compiz, I thought it was just part of it. Awesome that the pink isn't part of it.

**Update** This worked perfectly. I had to wait to get home from work to try it.

---

### Post by FredB on 2008-04-28
> **Alehbye said:**
> I'm pretty new to Compiz as the system I just built was a Windows machine, but when I converted it this weekend and started using Compiz, I thought it was just part of it. Awesome that the pink isn't part of it.

Looks to be a Nvidia 8xxx GPU driver bug only.

---

### Post by emiln on 2008-04-28
I had this issue(8800gts), and this solved it. Thanx alot!

---

### Post by alsamman on 2008-04-28
It's an emerald problem because I noticed that it went away when I switched to GTK window decorator. All I did was go to emerald themes, Edit, frames/shadows, and make opacity 0.01 and it went away as soon as i did that. I havent gotten glow ever since.

---

### Post by StefAndrew on 2008-04-28
Something I did made it want to boot into low graphics mode.  So I'll have to try the command again I guess from recovery mode...

---

### Post by randomAccess on 2008-04-28
And I thought this was some new 8.04 annoying desktop effect :lolflag::lolflag:

---

### Post by Polocoste on 2008-04-28
Thanks!!! Worked for me

---

### Post by alexsabree on 2008-04-28
Thanks a lot man, this was driving me nuts!!!

Thought they would fix this problem before they released 8.04 LTS, guess not. :KS

---

### Post by geoken on 2008-04-29
Awesome, can't wait to try this when I get home.

I just wanted to note that I don't think the problem is related to emerald. I ran 8.04 for 2 days (clean install) before installing emerald and intermitently saw the infamous 'pink shadow'. I actually installed emerald to try and get rid of this.

---

### Post by Pixel on 2008-04-29
Worked for me, great work!

---

### Post by marmiteOlz on 2008-04-29
tried it and it works ( 8800gts 512mb) 
however  it might be coincidence but....
my firefox 2 and 3 beta 5  both grey out and freeze then resume what they were doing a few mins later
cpu usage normally sits on 50%  when this happens( dual core so maybe 1 only freezing)

konqueror works fine 

ill keep using firefox and see if its a constant problem or just a intermittent problem. ps. only happened after i did the pink shadows removal process as described in this thread

---

### Post by Boyohazard on 2008-04-29
> **dirtysnachez said:**
> So, after banging my head for weeks trying to fix the weird glowing pink & yellow borders / no shadow issue on Hardy and Nvidia 8xxx cards.. I came across a simple solution from a guy on the nvnews forum. 

It involves removing a badly linked .so file from the Nvidia driver and re-symlinking it to the X server core instead. Go figure.. ?
<snip>
Worked like a charm thank you!! :D

---

### Post by martvi on 2008-04-30
Thanks a lot. Solved!

---

### Post by mivo on 2008-04-30
Thank you. My previous 64-bit installation of 8.04 didn't have this problem, but the 32-bit install did, and I had briefly wondered if it was intended to be so. ;) Very much appreciate the fix (hopefully it won't break anything down the road).

---

### Post by FuturePilot on 2008-04-30
....

---

### Post by KimH on 2008-05-01
> **randomAccess said:**
> And I thought this was some new 8.04 annoying desktop effect :lolflag::lolflag:

Me too:lolflag:

Thanks for the fix. It looks a lot better now.

---

### Post by spinanicky on 2008-05-02
Yoooour The Mannnn :d

---

### Post by Schizoid on 2008-05-02
This fixed my pink dropshadow issue. But is there a link to an actual bug report or something. There should be a proper fix somewhere for this. other then have to remove libs and symlinking . Even though I'm glad this fixes the issue.

On a side note. I'm still not getting composite shading when a gnome-terminal bell is fired. Anyone else have this problem. 

ie. hit tab a couple of times in gnome-terminal your terminal should pulse to gray .

my video card  GeForce 8400 GS

---

### Post by WiFi Ed on 2008-05-02
Thanks for posting this fix, it's working fine for me (so far!).

---

### Post by Psy-Krow on 2008-05-03
awesome,  thanx for the fix!!

---

### Post by psyeye on 2008-05-04
> **Schizoid said:**
> This fixed my pink dropshadow issue. But is there a link to an actual bug report or something. There should be a proper fix somewhere for this. other then have to remove libs and symlinking . Even though I'm glad this fixes the issue.


Found on launchpad - you might want to watch progress there: [https://bugs.launchpad.net/ubuntu/+source/compiz-plugins/+bug/216999]("https://bugs.launchpad.net/ubuntu/+source/compiz-plugins/+bug/216999")

psyeye

---

### Post by webitech on 2008-05-04
> It involves removing a badly linked .so file from the Nvidia driver and re-symlinking it to the X server core instead.

If you are using the "Nvidia X server settings" utility, this fix will break it. Your shadows will look normal, but you won't be able to use anti-alias or any other useful features you graphic card is capable of.

---

### Post by FuturePilot on 2008-05-04
Similar bug report
[https://bugs.launchpad.net/bugs/186382]("https://bugs.launchpad.net/bugs/186382")

---

### Post by Boyohazard on 2008-05-05
The last update caused a return of the pink shadows for me. FYI you can re-apply the fix in this thread to return things to "normal"

---

### Post by _godbout_ on 2008-05-06
I decided to look for a solution when I heard myself starting dating guys...
Now, everything is back to normal! :D

---

### Post by Amaranth on 2008-05-06
We only include nvidia's libwfb because originally 8xxx cards needed it to work at all and it seems it is still needed for some cards and for nvidia-settings to work so this is not a proper fix.

---

### Post by lars-5 on 2008-05-07
so is there a bug fix coming out then?

edit: just read the bug report... looks like some people solved it by manually installing the driver from nvidia

---

### Post by mivo on 2008-05-07
> **Amaranth said:**
> We only include nvidia's libwfb because originally 8xxx cards needed it to work at all and it seems it is still needed for some cards and for nvidia-settings to work so this is not a proper fix.

For many of us it is vastly better than no fix and having to wait until the next release to get rid of the pink and white shadows. :)

---

### Post by Separ on 2008-05-07
It is probably easier to just go into emerald, change the theme to something else and back again. At least that does it for me.

---

### Post by CorruptNoob on 2008-05-07
> **marmiteOlz said:**
> tried it and it works ( 8800gts 512mb) 
however  it might be coincidence but....
my firefox 2 and 3 beta 5  both grey out and freeze then resume what they were doing a few mins later
cpu usage normally sits on 50%  when this happens( dual core so maybe 1 only freezing)

konqueror works fine 

ill keep using firefox and see if its a constant problem or just a intermittent problem. ps. only happened after i did the pink shadows removal process as described in this thread


I just followed instructions in OP's post... and same thing is happening..

---

### Post by CorruptNoob on 2008-05-07
> **CorruptNoob said:**
> I just followed instructions in OP's post... and same thing is happening..

Had to restore my previous settings, the fix made my CPU get drained no matter what I did.

---

### Post by Amaranth on 2008-05-07
This is apparently fixed in the -17.36 version of the package and is currently building. It should be in hardy-proposed soon if it isn't already.

---

### Post by duddy on 2008-05-07
Worked perfect for me and my EVGA 8800GT 512!

---

### Post by fede on 2008-05-08
Thanks.

---

### Post by can8dnSix on 2008-05-09
LoL, well that explains it. Used the 0.01 opacity stated above and that seems to have fixed this little issue. thanks.

---

### Post by Zelandeth on 2008-05-09
Worked like a charm.  Cheers.

---

### Post by spyder0080 on 2008-05-10
ArchLinuxFan, thanks a lot for your solution! it worked!

---

### Post by colascorp on 2008-05-14
It works for me too. Many thanks!

---

### Post by durand on 2008-05-14
Lol, thanks for that :D

---

### Post by No-Neck on 2008-05-17
Great! I was starting to get annoyed with having to change theme 3 or 4 times every boot to get rid of the multicoloured glows. I noticed a couple of other threads about this that haven't been answered so I thought this could do with a slight bump.

Thank you!

---

### Post by rsaavedra on 2008-05-17
Thanks a lot, worked great for me!  I was surprissed when realizing how annoying that pink glow had become.  Tried to changed it with settings and didn't find where, a search with Google brought me to this thread.  Thanks again!

---

### Post by Scruffynerf on 2008-05-17
Big thanks here as well.

Also, this has also fixed the problem that the Nvidia 169.xx drivers have when rapidly scrolling forums with interchanged post colours.

6800GT card, Metacity, Hardy Heron.

---

### Post by RedRat on 2008-05-18
Thanks. I am running a Nvidia GT8600 on a Dell 530n, thought it was something new! The fix worked!

---

### Post by naraic on 2008-05-19
Worked for my 8400m gs.
Thank you! :)

---

### Post by S_Mitch on 2008-05-19
Wow, I love you.  Thank you so much!  That pink glow was driving me insane!

---

### Post by netron on 2008-05-20
thanks for the tip - this worked flawlessly for me. 

and there was me thinking that this "pink" thing was some sort of new compiz glow effect...

thanks!

---

### Post by multisimple on 2008-06-25
> **ArchLinuxFan said:**
> So, after banging my head for weeks trying to fix the weird glowing pink & yellow borders / no shadow issue on Hardy and Nvidia 8xxx cards.. I came across a simple solution from a guy on the nvnews forum. 

It involves removing a badly linked .so file from the Nvidia driver and re-symlinking it to the X server core instead. Go figure.. ?

*Instructions : *

- Open a terminal window.

- Type: **sudo rm /usr/lib/xorg/modules/libwfb.so**

- Then type: **sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so**

- Restart X (either reboot or "Alt-Ctrl-Backspace")

Now you can enjoy Hardy in all its proper black drop-shadowy goodness. \\:D/

Let me know if this works for you - [read original discovery thread]("http://www.nvnews.net/vbulletin/showthread.php?t=109546&page=2")

WARNING
This will destroy Xserver, and render your video display useless.
if you have already done so :(
start Ubuntu in recovery mode
Simply during boot press ESC for extra bootup options select recovery
after it boots select fix xserver, then the first option, normal boot up
once inside 
download **libwfb.so** from
[http://www.megaupload.com/?d=UIHNBLVI](http://www.megaupload.com/?d=UIHNBLVI)
save it some where
then open nautilus
```
sudo nautilus
```
navigate to libwfb.so copy and paste it to
/usr/lib/xorg/modules/

you may need to enable your video card inside System >> Administration >> Hardware Drivers or reinstall your video driver

---

### Post by Elycian on 2008-09-05
@Multisimple

Totally saved me man, thanks :]

---

### Post by Na$$im on 2009-03-03
Thanks a lot Multisimple ! you saved my ubuntu !;)

---

