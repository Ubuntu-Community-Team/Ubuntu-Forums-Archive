---
title: "instaling blender?"
date: 2007-05-06
forum: General Help
---

### Post by hessiess on 2007-05-06
ive downloaded a linux build of blender from blender.org, but how do i install it. its a semi working dual boot of windows/ ubuntu on a hp pavilion dv2000. there is no internet connection from ubuntu, and i doubt there ever will be becose it wont recognise the wireless network card. linux is sppost to render faster than windows, witch is part of the resen why i wanted to try it. other part is windows is becoing extremely slow and i like the idea of open scorce software. but without blender i carnt do a thing with ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=433706"]
incase your wandering what i meen by semi working see this thred (link)[/URL]

---

### Post by DeadEyes on 2007-05-06
It should just be a case of extracting the files from the archive to whatever directory you want. Then open a terminal cd to that directory and type ./blender

---

### Post by peebly on 2007-05-06
Hello

Can you not install blender from synaptic, just type blender in search.

Or

Its under graphics in add/remove.

sorry, I see, just read your post correctly. Doh

---

### Post by hessiess on 2007-05-07
somone on blenderartists sed:


> Ubuntu doesn't come with all the necessary dependancies to run Blender. You need to download all the dependencies. Try asking on the Ubuntu forums for how to find out what the dependencies are.

what are these?

---

### Post by DeadEyes on 2007-05-07
what happens when you try to run it?

If you have a look [here]("http://packages.ubuntu.com/feisty/graphics/blender") you'll see a list of dependencies. It looks like there is quite a lot of them but I am nearly certain that all, or nearly all, of them should  already be on your system.

I've installed blender from both the repos and the blender site,when newer versions are released, and I don't recall having to download anything extra. Blender comes in two flavours for linux, well four but thats not important right now. There is a static and a dynamic build. The static includes all the dependencies that blender  needs so try that one, if you really are having dependency issues.

---

### Post by hessiess on 2007-05-07
> **DeadEyes said:**
> what happens when you try to run it?

If you have a look [here]("http://packages.ubuntu.com/feisty/graphics/blender") you'll see a list of dependencies. It looks like there is quite a lot of them but I am nearly certain that all, or nearly all, of them should  already be on your system.

I've installed blender from both the repos and the blender site,when newer versions are released, and I don't recall having to download anything extra. Blender comes in two flavours for linux, well four but thats not important right now. There is a static and a dynamic build. The static includes all the dependencies that blender  needs so try that one, if you really are having dependency issues.

it just wont start. ive got the 2.44 pre relece verson for linux.

---

### Post by DeadEyes on 2007-05-07
I downloaded blender-2.44RC2-linux-glibc232-py24-i386 and I didn't have any problems.
Sorry I can't think of anything else that might help.

---

### Post by djorzgul on 2007-06-03
hey, I thoought to post here instead of opening new thread.
I installed blender via add/remove apps and it is v2.43. There is 2.44 for download on blender.org, so aprox. how long does it take that update appears among ubuntu updates?

---

### Post by hessiess on 2007-06-04
just download blender forom blender.org and stick it somwere. you canot click on blend files to start it. but it wolrks perfectly, with the deb it cept demanding dependencys. 

unless you are quite advansed with 3d art then 2.44 has nothing to offer you. its mostly bug fixes. and a sss shader on the internal renderer+ afew more primatives.

---

### Post by msmithy12 on 2007-06-06
i know tht the oridginal poster has no network connection, but i have a network connection can i install blender from terminal?
 possibly

sudo apt-get install blender
????

---

### Post by hessiess on 2007-06-06
you can but i think you would get 2.43. its quite easy to set up from the blender.org tarball

---

### Post by TKR101010 on 2007-08-01
Greetings all,

I've just switched to Ubuntu, and have Blender installed from the repositories, but it's an out of date version. So I have downloaded the files from Blender.org for the new version. I'm fairly confident that I'll be able to install the new version (and if not I'll be seeking help later).

Being new to Ubuntu (and linux in general), my questions are ...

1. Do I need to uninstall the old version before installing the new version?
2. If I don't have to uninstall the old version, will installing the new version automaticly overwrite the old version, i.e. use the same directories and such and replace the old files with new ones?

Thanks for any info,

TKR101010

---

### Post by hessiess on 2007-08-01
just unzip it to your home directory and run it from there, works perfect.

then just right click on a blend file and brouze for the new blender executoble, should then atomaticly open with newist version

---

