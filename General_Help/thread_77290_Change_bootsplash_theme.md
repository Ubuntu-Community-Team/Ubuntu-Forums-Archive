---
title: "Change bootsplash theme?"
date: 2005-10-16
forum: General Help
---

### Post by matthias_k on 2005-10-16
Hi,

cool that the stock Breezy kernel has the bootsplash patch, but as much as I love this distro, I really dislike its brownish themes everywhere.

So where/how can I change the bootsplash theme? I have never worked with a Linux which had a bootsplash so far but I guess there is a way to modify it?

Thanks.

---

### Post by duffman25 on 2005-10-16
[QUOTE=matthias_k]Hi,

cool that the stock Breezy kernel has the bootsplash patch, but as much as I love this distro, I really dislike its brownish themes everywhere.

So where/how can I change the bootsplash theme? I have never worked with a Linux which had a bootsplash so far but I guess there is a way to modify it?

Thanks.[/QUOTE]

The package you're talking about is called usplash and there's a customization guide in the wiki:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

Hope it helps, I haven't tried it out.

---

### Post by Muhammad on 2005-10-16
You can disable bootsplash by using the command:

```
sudo apt-get remove usplash
```

---

### Post by matthias_k on 2005-10-17
Thanks for that link, but I tried to get my hands dirty and create my own usplash theme and I utterly failed (I just can't handle GIMP), I don't even know how to create a limited palette properly.

Aren't there any usplash themes on the net? ^^
I googled but didn't find anything specific. Even on gnome-look.org I didn't find anything. I had expected that there are tons of usplash themes, since it's not Ubuntu specific right? This bootsplash kernel patch has been around for years. Many other distros use it since quite some time before Ubuntu did.

Hmmm, on a second thought: Maybe I'm confusing bootsplash with usplash? Are these two different (read: incompatible) ways of showing a splash screen? Do themes for one work with the other at all?

---

### Post by matthias_k on 2005-10-17
Soooo, I finally managed to make my own theme. I don't know, the possibilities are rather limited with a 16 Bit color palette so it doesn't look as clean as I'd like it to be. I did a interlace-effect on the ubuntu logo which I actually don't really like, but the edges were pretty rough so I tried to cover that.

Tell me if you like it, or better yet, come up with something cooler. My GIMP skills are really on the low-end. I have also written a script which does the required steps to change your usplash image. You simply have to type:
```
$ sudo ./make-usplash yourimage.png
```
That's it. Of course your image has to comply to the specifications pointed out in the link posted above. Really, I don't know what will happen if it doesn't so better stick to it.

[[IMG]http://img91.imageshack.us/img91/8648/usplash5qf.th.png[/IMG]](http://img91.imageshack.us/my.php?image=usplash5qf.png)

By the way, that guide in the Wiki is incomplete. It seems to me that usplash separates between the text on the left side (what action is currently taken) and the status on the right side (OK, Failed, etc). When I set the text color according to the Wiki, only the status text was affected, but the action text was still black. Since I didn't want to test which of the 16 slots was reserved for the action text, I just set all left slots to the same color, and it worked. Pretty lame, I know.

Anyway, tell me what you think.

---

### Post by shiny sunbird on 2005-11-11
You're really on the way :p .
Perheps you could improve your GIMP skills by checking out TuxMagazine. In the march, may, june and july issues there is an easy GIMP-t:cool:ur.

---

### Post by Haegin on 2005-11-15
While on the subject of themeing usplash - is it possible in any way to remove the text and move the progress bar? (Changing colours isnt an option - its a photo im using (I know about the 16 colour limit))

Thanks for all the help

A tip that I learnt when trying to make a grub splash for anybody who isn't so up with the gimp:
To reduce the number of colours look under Image > Mode > Indexed...

---

### Post by alexmap on 2005-12-02
[QUOTE=Muhammad]You can disable bootsplash by using the command:

```
sudo apt-get remove usplash
```[/QUOTE]

You can also just edit your /boot/grub/menu.list file -- just remove the word "splash" (shown in bold).

```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet **splash**
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

to

```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

I personally dislike seeing the brown Ubuntu bootsplash when I turn on my computer, and I found this was a quick and easy way to turn it off.

---

### Post by matthias_k on 2005-12-02
Yeah. To be honest, I'm not using my own theme anymore either, I also switched back to text-based mode. I'd rather look at nice text than at ugly graphics. :)

---

### Post by KermitJr on 2005-12-05
[QUOTE=matthias_k]Yeah. To be honest, I'm not using my own theme anymore either, I also switched back to text-based mode. I'd rather look at nice text than at ugly graphics. :)[/QUOTE]
No comment on how messed up that is! ;)

I'm' sure that's why splashes exist --- "I really like text mode, but I'm make some ugly graphics instead...."

Cheers!
KJ

---

### Post by modemsutra on 2006-04-26
thank you man !! I wanted to see what happened during the boot this splash is nice but I need to see the boot process to optimize it thanks for the tip!!

---

