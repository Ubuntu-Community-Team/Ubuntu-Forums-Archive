---
title: "How can I install VMWare + Vista?"
date: 2007-10-14
forum: General Help
---

### Post by Mr. Johnson on 2007-10-14
If I install VMWARE and Vista, will I be able to boot up Ubuntu 7.10 and start Vista and then install Adobe Lightroom? :confused:

---

### Post by crevan on 2007-10-14
My suggestion would be to install Virtual Box instead. I've it running XP at home, with a few adobe programs installed on it. And best of all, in my opinion, once you get it installed, you can install "guest addons" and hit Ctrl+L and run seamlessly.

[QUOTE=User from another site]Alright, I'm assuming you have Ubuntu 7.04 Feisty Fawn:

First, you need a virtualizer. 

Download Virtualbox 1.5 here: [http://www.virtualbox.org/download/1.5.0/virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb](http://www.virtualbox.org/download/1.5.0/virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb)

If you have an AMD 64 Bit Machine, get this one instead: 

[http://www.virtualbox.org/download/1.5.0/virtualbox_1.5.0-24069-1_Ubuntu_feisty_amd64.deb](http://www.virtualbox.org/download/1.5.0/virtualbox_1.5.0-24069-1_Ubuntu_feisty_amd64.deb)

Now, following the installation instructions here: 

[http://www.howtoadvice.com/UbuntuVirtualBox/](http://www.howtoadvice.com/UbuntuVirtualBox/)

At this point, you need to choose an OS to install into Virtualbox. Although it is certainly possible to install really any Windows you wish, I recommend a stripped down version of Windows Server 2003. 

Of course, this is all assuming you have a license to the full version, but I'll leave that to you :)

Now, you have two choices here:

Micro2003 0.7

Tiny 2003 Enterprise (or Datacenter) 

Both 'flavors' are created by eXPerience. 

The first is incredibly stripped - only 110 mb of installation files. Idling, it uses about 38 mb of ram, compared to about 200 of XP. The only issue is that it doesn't support home networking, meaning that you won't have any file transfer between Ubuntu and Windows aside from a shared copy/paste clipboard and mounting image files made in Ubuntu as a CD in Windows. 

If you plan to do file creation and the like and absolutely require cross platform file transport on a frequent basis, then you should look to Tiny2003. 

Tiny2003 is more 'feature-complete', that is, it has less stripped out of it than Micro2003. Where Micro2003 is missing many features (No Webcams, Scanners or Digital Cameras, multiuser, the annoying autoplay, scheduled things, or themes) Tiny2003 can do whatever XP can do. This comes at some additional overhead and a slightly slower boottime compared to the insane 15 seconds of Micro2003. 

However, keep in mind that if you have more than a gig of ram and you want total convenience, you can also run a normal installation of XP as well, though I think it's a waste. The stripped down version of Server2003 lack many things that the host OS (Ubuntu) already has, cutting down on redundancy. 

The process of installing an OS into Virtualbox is fairly straightforward and shouldn't take explanation, but if you find yourself in need, just make another post. Just keep in mind that Micro and Tiny need 130 Mb and 150 Mb of allocated ram to function smoothly. You can always increase this amount later if it is too little for what you run. HD allocations are up to you, but I suggest 5 GB at the minimum. 

When everything is installed, and you can see the Windows desktop in the Virtualbox window, install the VBOXADDITIONS software in windows through the top menu in the OS window. This allows the shared clipboard and unified mouse features. When this is the done - and the following is the best part of it all - you can press Right Ctrl + L  to make a seamless desktop like the one I have: 

[U][http://img255.imageshack.us/img255/6869/screenshotdm5.jpg](http://img255.imageshack.us/img255/6869/screenshotdm5.jpg)

[/U]  If you have Beryl, Compiz, or Compiz Fusion, you need to install Google desktop on the guest Windows OS and keep the same wallpaper for both systems. This keeps a certain bug away in this set up that will likely be fixed in the newest update of Virtualbox. 

I'll be around if you need additional help.[/QUOTE]

Pretty easy to follow, really. I'm using 7.10 and this worked perfectly for me.

---

### Post by -grubby on 2007-10-14
yes, but remember that you can only run Vista Ultimate in a VM as Microsoft crippled the other versions that cost less

---

### Post by AbredPeytr on 2007-10-14
You can also run Vista Business with vitural software.  Pain in the butt not being able to virtualize the Home edition, which most home users will have.  

Try to run the program under Wine or Cedega instead, or find a Linux version to replace it.

---

