---
title: "I cant install vlc"
date: 2007-10-04
forum: General Help
---

### Post by nfs2192 on 2007-10-04
**This post could be related to an Ubuntu bug filed at**: nfsmw21 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				each time i try to install vlc it keeps saying i need another file and i keep geting them but now its stoped at **_libc6_** its installed but it keeps saying its not and when i downloaded it and tried to install it said that and eairler version is already installed do anyone know whats up???

---

### Post by rsambuca on 2007-10-04
What method are you using to try and install this.  All you should have to do is use Synaptic Package Manager.  Just make sure your Universe Repository is selected first, and then select vlc and click apply.

---

### Post by nfs2192 on 2007-10-04
i dont know what im doing i just downloaded the file and tring to install it from there and it keeps saying dependency is not satisfiable...............and that i need a pakage but how do i get to the Synaptic Package Manager and the Universe Repository

---

### Post by strabes on 2007-10-04
Just run this command:```
sudo aptitude update && sudo aptitude install vlc
```

If it doesn't work, paste the output. If it does, tell us.

---

### Post by nfs2192 on 2007-10-05
als o each time i try to install libc6 it says i already have a new one installed........but vlc keeps saying i need it

---

### Post by Daveth on 2007-10-05
Synaptic package manager, which you should know about independently of the apt-get terminal commands (as this requires you to know what you want to install) lives in System/ Admin/ Synaptic Package Manager. Put in your password and then just browse about, or use the search option. 

So, if you put vlc in the search box, it will hunt down Ubuntu's vlc deb package. You can then download from there- it trawls for all the dependcies, such as your libc6 library file. 

As Strabes notes though, you do need to make sure your repositories, where such things are stored, are available. You get to this part of your system by System/Admin/software sources, and check that all the sources on the front page are checked (too many "checks in that sentence!).

In combination these will give you access to a huge range of programs that mostly just work, and are often a surer bet than trying it from scratch, especially if you are starting out. It also allows you to easily remove stuff, via the right click in Synaptic. Easy peasy:)

---

### Post by nfs2192 on 2007-10-10
what......lol that sounds complicated do anyone know what files i need to get the totem movie player(or whatever player that comes with ubuntu) to play retail DVDs and MP3s.

---

### Post by zvacet on 2007-10-10
> what......lol that sounds complicated

Few clicks sounds complicated?Youst follow Daveth advice and you will be suprised how easy it is.

---

### Post by nfs2192 on 2007-10-11
yes it do how u get to System/ Admin/ Synaptic Package Manager cause the computer b dening me acsess to some stuff like deleting files but still how do i get to System/ Admin/ Synaptic Package Manager

---

### Post by por100pre1 on 2007-10-11
Please read this [how to]("http://ubuntuforums.org/showthread.php?t=413625") carefully. Let us know if it is not enough.

---

### Post by nfs2192 on 2007-10-15
man ppl notings helpin me i think cause i need internet acsess but do anyone now what files i can download to get totem to play mp3, mp4 and retail dvd's i can download files at my friends house but i need to kno what files i need.........

---

### Post by nfs2192 on 2007-10-15
this is not helpin do anyone kno what files i need to download to play mps, mp4, and dvds cause i dont have internet acess at home

---

### Post by zvacet on 2007-10-15
> gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs
You can find it here 

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

be sure that you download packages sign with red ball(they are dependencies)and when you go to install install them (red marked)first.

and w32 codecs wich you can find at

[http://packages.medibuntu.org/pool/non-free/w/]("http://packages.medibuntu.org/pool/non-free/w/")

---

### Post by nfs2192 on 2007-10-16
finaly some help but can u split them up more so i no what im searching for thanx

---

### Post by zvacet on 2007-10-16
I´m glad I can help.Maybe you find this helpfull too.

[http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet]("http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet")

---

### Post by nfs2192 on 2007-10-17
one more thing the red dots that mean i need to get them to???

---

