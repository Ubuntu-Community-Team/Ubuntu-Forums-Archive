---
title: "Playing Mp3 Files"
date: 2005-10-13
forum: General Help
---

### Post by cparsons on 2005-10-13
I have just installed Linux Ubuntu on my laptop - its great!, but i plugged in my mp3 player, and "Music Player" said that it didn't support the file MP3! 

What can i download to play MP3's on my laptop, as i have a presentation to give tommorrow!!!

---

### Post by Wolki on 2005-10-13
[QUOTE=cparsons]I have just installed Linux Ubuntu on my laptop - its great!, but i plugged in my mp3 player, and "Music Player" said that it didn't support the file MP3! 

What can i download to play MP3's on my laptop, as i have a presentation to give tommorrow!!![/QUOTE]

Everything you need to know: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Follow the instructions "Getting started" and "Codecs and DVD-Video". If you encounter any problems, feel free to ask.

---

### Post by cparsons on 2005-10-13
okay, i have no idea what that all meant.... i did the first step - in synaptic package manager,but after that i lost it...

i kind of need a quick and permament solution - like a programme that i can download so that i can simply play my MP3s at my confrence presentation tomorrow.

any ideas?

---

### Post by cparsons on 2005-10-13
adding to last message...

i.e where would i find the plugin needed to play the mp3 file in Music Player?

Sorry, but i am in a serious rush to get this presentation ready!

---

### Post by Wolki on 2005-10-13
OK, so a little more details...

If you managed the first part (adding repositories), you have it nearly solved.

You can actually leave some of the other instructions out, unless you need quicktime/windows media support.

Close synaptic if you have it open. Open a terminal (Hoary: Applications -> System Tools, Breezy: Applications -> Accesories) and paste the following:
```

sudo apt-get install totem-xine gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-mad gstreamer0.8-ffmpeg libmad0 msttcorefonts libdvdread3
```
Enter your password if it asks you.

If this command-line things scare you, you can also start synaptic and search for each word after "sudo apt get install" (ie totem-xine. gstreamer0.8-misc etc) and check the checkbox in front of the name. If you're done, click apply. This way will take longer, but end with the same result as the command above)

After that you have a ton of different codecs installed. You just need to tell the system that they're there now. In the terminal, paste "gst-register" (without quotes). After that you're done, try and see if it works

If you don't want to use the terminal. hit Alt-F2, and paste "gst-register" in the window that appears. Hit enter.

Again, problems or questions? just ask.

---

### Post by cparsons on 2005-10-13
okay, i have done that, but then this came up...

package totem-xine is not available, but is referred to by another package. this may mean that the package is missing, has been obsoleted or is only available from another source
E: Package totem-xine has no installation candidate

(hope i copied that out right!)

what does that mean?

---

### Post by Wolki on 2005-10-13
[QUOTE=cparsons]okay, i have done that, but then this came up...

package totem-xine is not available, but is referred to by another package. this may mean that the package is missing, has been obsoleted or is only available from another source
E: Package totem-xine has no installation candidate

(hope i copied that out right!)
[/QUOTE]

This means you didn't setup your repositories correctly. Take a look here again: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and make sure you followed the graphical tutorial on enabling universe and multiverse exactly.

Ubuntu looks for files to install in a database. It's very easy to use and fast, but you have to point it at the correct database :) (An interesting comparision of program installation on windows and ubuntu is here: [http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php))

Note: Installing totem-xine will tell you that this will remove something called "ubuntu-desktop". Don't wory, this isn't bad, but you should reinstall that package before you do a version upgrade with ubuntu (like hoary->breezy). I can explain to you why if you're interested. If this is too much of a hassle for you, you don't need totem-xine to play mp3s. Just remove it from that command, so it'll look like:

```
sudo apt-get install gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-mad gstreamer0.8-ffmpeg libmad0 msttcorefonts libdvdread3
```

---

### Post by cparsons on 2005-10-14
now it is saying that gstreamer0.8-plugins has no installation candidate???

---

### Post by Wolki on 2005-10-14
OK, post the contents of your "/etc/apt/sources.list" file. This way we can check where the problem with your repository setup is.

---

### Post by cparsons on 2005-10-17
[QUOTE=Wolki]OK, post the contents of your "/etc/apt/sources.list" file. This way we can check where the problem with your repository setup is.[/QUOTE]

sorry it has taken so long to get back to you, but phone connection in my area has been down.

where would i find this list? i seem to have lost track of where we were going:confused:

---

### Post by Wolki on 2005-10-17
[QUOTE=cparsons]sorry it has taken so long to get back to you, but phone connection in my area has been down.

where would i find this list? i seem to have lost track of where we were going:confused:[/QUOTE]

No problem.

Let's try the following first:

Start Synaptic. Go to settings -> repositories, Add, and check the two options "universe" and "multiverse". OK. It should tell you that it needs to reload the repositories, confirm that. If you try to install gstreamer-plugins now it should work.

If it doesn't, open a terminal and paste "cat /etc/apt/sources.list" into a terminal and post the output here.

---

### Post by cparsons on 2005-10-19
[QUOTE=Wolki]
Start Synaptic. Go to settings -> repositories, Add, and check the two options "universe" and "multiverse". OK. It should tell you that it needs to reload the repositories, confirm that. If you try to install gstreamer-plugins now it should work.

If it doesn't, open a terminal and paste "cat /etc/apt/sources.list" into a terminal and post the output here.[/QUOTE]

slight problem... i don't have an internet connection on my Linux laptop - i use my windows PC for that at the moment, as the internal modem won't work with Linux. 

so, basically it couldn't do anything. 

but for my clarification are you sure there isn't a programme available to download that will play the mp3 file, as the file is now recognised, it just wont play.

---

### Post by doclivingston on 2005-10-19
[QUOTE=cparsons]but for my clarification are you sure there isn't a programme available to download that will play the mp3 file, as the file is now recognised, it just wont play.[/QUOTE]

Rhythmbox (Music Player) is loading your files, but can't play them? That is odd.

Can you run ```
gst-inspect-0.8 mad
``` in a terminal, and see whether it prints out "No such plugin or element" or a heap of info? (don't bother putting the info here, just see whether it prints it)

---

### Post by Wolki on 2005-10-19
[QUOTE=cparsons]slight problem... i don't have an internet connection on my Linux laptop - i use my windows PC for that at the moment, as the internal modem won't work with Linux. 
[/QUOTE]

Ah, ok, didin't know that. In that case, it's probably best to get the hoary addon cd at [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/) . It's a bit large, but contains a lot of often used files, including codecs.

If you're using breezy, don't know if there's a similar cd already.

If getting that cd is not an option, go to packages.ubuntu.com and search for gstreamer0.8-mad; download the one for your version of ubuntu and check whether you have all the dependencies installed (there's a lit of required files at the site; you can see in synaptic which packages you already have installed. Download these dependencies in the same way (ie checking for their dependencies).
Then copy then to your linux computer and run "sudo dpkg -i <filename>" for each of the files, dependencies first.

This is a bit complicated, and can get out of hand fast. Ubuntu is not yet great for computers without internet access, let's hope some things can be changed in the future. It should not be that difficult for mp3 support though, there's not a lot of additional dependencies that should have.

---

### Post by cparsons on 2005-10-20
[QUOTE=doclivingston]Rhythmbox (Music Player) is loading your files, but can't play them? That is odd.

Can you run ```
gst-inspect-0.8 mad
``` in a terminal, and see whether it prints out "No such plugin or element" or a heap of info? (don't bother putting the info here, just see whether it prints it)[/QUOTE]

it states: "No such element or plugin 'mad'

---

### Post by cparsons on 2005-10-20
[QUOTE=Wolki]Ah, ok, didin't know that. In that case, it's probably best to get the hoary addon cd at [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/) . It's a bit large, but contains a lot of often used files, including codecs.[/QUOTE]

so this addon cd would be a download, and therefore you can't get a hard copy of the cd?

---

### Post by doclivingston on 2005-10-20
[QUOTE=cparsons]it states: "No such element or plugin 'mad'[/QUOTE]

That means that the gstreamer plugin isn't installed correctly, try the following:

1) check synaptic to make sure that "gstreamer0.8-mad" is installed,
2) if it is, open a terminal and run "sudo gst-register-0.8" followed by "gst-register-0.8"

Occasionally the registry doesn't update properly, meaning that the plugin doesn't get installed. One good thing about gstreamer 0.10/1.0 (in addition to much better a/v sync) is that the registry is gone, so you won't have to worry about this in Dapper.

---

### Post by cparsons on 2005-10-20
i have been looking at packages.ubuntu.com and i have worked out that the following programmes are missing: 

libgstreamer0.8-0
libid3tag0 
libmad0 

now, this might sound stupid, probably because it is, but how do i work out which architecture i need? 

there is a choice of amd64, i386 and powerpc. 

resorting to the user's manual, i know the processor is a 650MHz Mobile Intel Celeron, but is this even what i have to match the download to?

---

### Post by cparsons on 2005-10-20
[QUOTE=doclivingston]1) check synaptic to make sure that "gstreamer0.8-mad" is installed[/QUOTE]

i ran a search in synaptic and (surprise, surprise) the file didn't show up.

but now i get a warning when i start up:

"W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)"

i can't remeber if it was suggested to install this on this forum, or by an I.T person from my work, but do i need to get rid of it, and therefore, how?:confused:

---

### Post by doclivingston on 2005-10-20
Look at /etc/apt/sources.list, you should have a line somwhat similar to the following, although you might not be using the Australian mirror, and the universe line might be seperate from main and restricted.
```
deb http://au.archive.ubuntu.com/ubuntu hoary main restricted universe
```

From the look of the error, I'd say you are missing the "ubuntu" off the end of the main address.

---

### Post by cparsons on 2005-10-20
[QUOTE=doclivingston]Look at /etc/apt/sources.list, you should have a line somwhat similar to the following, although you might not be using the Australian mirror, and the universe line might be seperate from main and restricted.
```
deb http://au.archive.ubuntu.com/ubuntu hoary main restricted universe
```

From the look of the error, I'd say you are missing the "ubuntu" off the end of the main address.[/QUOTE]

why does it need an internet address though? my laptop isn't even connected:confused:

---

### Post by doclivingston on 2005-10-20
Sorry, I'm getting confused about which thread I'm in. If you're not connected to the 'net, either remove or comment out (prefix with "#") any lines from /etc/apt/sources.list which contain internet addresses.

The architecture you need if i386; powerpc is for Macs, and amd64 is for 64 bit AMD machines machines.

---

### Post by cparsons on 2005-10-20
okay, i have downloaded the files that i think i need, what do i do with them now?

---

### Post by doclivingston on 2005-10-20
use "dpkg -i file1.deb file2.deb ..."

---

### Post by cparsons on 2005-10-21
[QUOTE=doclivingston]use "dpkg -i file1.deb file2.deb ..."[/QUOTE]

and that entails what exactly...:???:

---

### Post by Narg on 2005-10-23
First of all, find where you have the file, (a cd, your home, etc), then open up a console/terminal program. Move to where they are using 'cd wheretheyare' and type 'dpkg -i package1.deb, package2.deb, etc' in, then type your password if prompted.

---

