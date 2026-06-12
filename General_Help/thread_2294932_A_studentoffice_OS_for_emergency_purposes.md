---
title: "A student/office OS for emergency purposes"
date: 2015-09-14
forum: General Help
---

### Post by ldvivier on 2015-09-14
Good day guys

My Windows PC recently crashed on me.  I am usually not concerned as I backup quite often.  Due to the nature of the crash I could however simply have continued working, sorting out the problem later, if I had an emergency, portable OS.  I study part time whilst working so being able to just 'get up and go' would have been nice.

What I was in need of therefore was:
1. An OS that I could just plug in and either run on or install from a flashdrive.
2. An OS that is small and not bloated with lots of extra stuff: I just need an internet browser (to get to my online study content) and an Office package (like OpenOffice) to do my work.  A file browser would be nice as well.  That is about it.  In such a pinch I do not need all the extra music and video editing and finance etc. etc. etc. software that usually comes along with it.

I have found linux distros online that can run on flash drives and are small...but they all seem obscure, do not appear to have LTS or do not have a full Office suite as standard.  Thus I am looking at Ubuntu as I would like, 3 years from now when I need to plug it in, be fairly sure the newest versions of the Office software are still supported if I do feel like downloading them.  But can you install Ubuntu on a flashdrive?

I have read online that you could make your own custom distros with only specific things in the package.  Could one do so with Ubuntu?  Can I build my required package somehow?

Any directions or suggestions would be greatly appreciated.  I have used Ubuntu in the past and would therefore like to stick to it instead of trying some other, random, small linux distro.

Regards

Leon

---

### Post by monkeybrain20122 on 2015-09-14
Any *buntu live usb with persistence would have fullfiled all your requirements.  For light DE use xubuntu. Libreofiice may not be installed, but easy to install it yourself with synaptic/software centre. Music players etc do get installed by default but since the whole OS takes about 5 G they don't take a lot of space anyway.

---

### Post by coldraven on 2015-09-15
Searching for "create persistent usb" brings up a lot of hits, here is one that covers your needs:
[http://linux.about.com/od/howtos/ss/How-To-Create-A-Persistent-Bootable-Xubuntu-Linux-USB-Drive.htm](http://linux.about.com/od/howtos/ss/How-To-Create-A-Persistent-Bootable-Xubuntu-Linux-USB-Drive.htm)

I have had good results from the Unetbootin installer and it runs on Windows/Mac/Linux, you can get it here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

P.S. Every flavour of 'Buntu can be found here, it may be wise to get the 32 bit version which should work on any PC. Get the Long Term Support (LTS) release for extended security updates.

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by mastablasta on 2015-09-15
besides what others have said...


> **ldvivier said:**
>   But can you install Ubuntu on a flashdrive?

Yes. Problme is SWAP partition, however you can install without or at least reduce swapiness it if you have enough RAM. so that for example it is not used unless you are taking up more than 90% RAM or something.

> 
I have read online that you could make your own custom distros with only specific things in the package.  Could one do so with Ubuntu?  Can I build my required package somehow?

yes, you can. there used to be an app for that. I am not sure what the new version is called anymore.  

there are also Ubuntu based flavours that are already minimalistic. like others said a live CD of those with some persistence added, then install office and you are good to go.

---

### Post by mystics on 2015-09-15
As others have mentioned, the Ubuntu solution is to use Xubuntu (or Lubuntu) on a USB with persistence. I'm not sure about Lubuntu, but Xubuntu does come with AbiWord and some spreadsheet software on 14.04, though I think they replaced it with LibreOffice on a more recent version or are planning to on the next one.

Also, depending on your office needs, you could always look into what Microsoft and Google offer with their online services. If those work, anything with a web browser would do.

---

### Post by ldvivier on 2015-09-23
Thank you very much to everyone for the responses! 
Sorry for my slow response - been a bit busy.

I figured that what I needed was something like Porteus.  Small, easy to install and run and comes with LibreOffice installed.  This is all I need to just get me online and continue working on my studies.

I will however definitely be looking into your other suggestions as I would like to improve my Dad's old PC that he is using as a media player. Windows is a bit bloated for this.  But I believe the base *buntu installations are as well.  Will possibly start with the MinimalCD and start from there.

Regards

Leon

---

