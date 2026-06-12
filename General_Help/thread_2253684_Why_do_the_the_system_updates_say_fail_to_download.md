---
title: "Why do the the system updates say fail to download ?"
date: 2014-11-21
forum: General Help
---

### Post by hebdave on 2014-11-21
High I get the fail to download message coming up when I download the repository with the GUI. Then I try the other option button and that does not solve it. Then I hit the option on the right saying "okay" and it does seem to give me something to download then and it installs it too. After this it says "no more updates" when I re-try everything again. But I still get an exclamation mark at the top of my workspace warning me to update correctly a little while later. A restart does not solve it. I am confused and not sure if all is as it should be. I have recently upgraded to 14.04LTS but am not sure if that is causing the problem. Many thanks.

---

### Post by nerdtron on 2014-11-21
You can try to see the updates and errors from the command line. Post the output of the command here.
```
 sudo apt-get udpate 
```

---

### Post by grahammechanical on 2014-11-21
It all depends. Sometimes we have installed software through a Person Package Archive (PPA). That is a useful way to install software that is not in the Ubuntu Software Centre but they may cause errors like this. Some PPAs, provide updates to the packages. Others do not. So, sometimes we need to disable those PPAs after the software has been installed.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

When we upgrade from one version of Ubuntu to a newer version we may still have PPA URLs listed as software sources. If the PPA has not been upgraded by the developer for that release of Ubuntu then the update process will throw up an error. 

What you could do is run these two commands and post any error messages (enclosed in quote tags) back here and then we will have a better idea of what in particular is throwing up these error messages.

```
sudo apt-get update
sudo apt-get upgrade
```

Those are the two commands that Software Updater runs but doing it a terminal gives us a bit more information than the simple "something is not right" message of Software Updater.

I always get that red exclamation mark. But then again, I am running the development version of the next release of Ubuntu (Vivid Vervet) and not all the repositories are online. For example, there is no need for a backports repository on a version that has not yet been released. But nontheless, that backports repository is in my list of software sources. It does not prevent updates from happening. I live with it. It is not something to worry about. But with a released version we can and should fix things like this.

Regards.

---

### Post by hebdave on 2014-11-26
> **grahammechanical said:**
> 

What you could do is run these two commands and post any error messages (enclosed in quote tags) back here and then we will have a better idea of what in particular is throwing up these error messages.



Sorry I don't understand forums well enough. Did you mean quote your last response and then put the errors in something else where you can see it better ? I have a whole host of stuff from the terminal but error appears half way in a code line. So it seems to me I need to give the full lines as well as what is says after the error ? 

This is what is says after sudo apt-get update is run ( the first paragraph is is shortened as I wasnt sure you needed the other bits ):

```
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ PackagesErr cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Packages
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/main amd64 Packages
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/main amd64 Packages
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/restricted amd64 Packages
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/restricted amd64 Packages


IF YOU NEED THE ABOVE BITS TO BE MORE COMPLETE I RECOMMEND ME REPOSTING ALL OF IT AT ONCE IF THAT CAN BE DONE IN A FORUM.

FROM BELOW ONWARDS IS THE ENTIRE CODE THAT IS GIVEN IN THE TERMINAL I THINK YOU CALL NANO OR SOMETHING-

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [72.8 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Fetched 2,227 kB in 10s (216 kB/s)                                             
W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Below is the part that looked suspect from sudo apt-get update  -

> Unknown media type in type 'all/all'Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

Thanks if its not done correctly for you let me know. If you need the full terminal read out of apt-get update let me know. Much appreciated :)

---

### Post by Bashing-om on 2014-11-26
hebdave; Hello

This:
> 
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ PackagesErr cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Packages

Do not know where this could pop up from, You are running 14.04 and release 12.04.3 has no relevance;
a) uncheck the box for CDrom in Software Sources GUI application
b) make sure the liveDVD is not inserted when updating the system
c) Then we need to look at the sources.list .
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

This:
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found

says that a requested file at the server " ppa.launchpad.net" can not be found. The outputs from above will provide a direction to see what is requested, and we can find out why the system can not comply.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-11-26
The second part does not really matter, it's common (ie the output stating unknown media types ,etc,etc)
The first part is where you have two things causing failure.
The first is you have the entries to access the cd, in this case it wants to access the 12.04 precise cd.
The second problem is you have two ppa, which may not have versions available for 14.04.

To solve, open the Program called "Software and Updates"
Go to the section "Other Software"
If we are lucky, we can solve both problems in here.
First look for any entries for cd-rom and uncheck them, if they do exist.
Then go down and find the entries for the two ppa's( It'll be four entries, really; because you have sources enable for them as well)
The two should be for mizuno and for shnatsel.
Uncheck all entries with those two names.
Then close the window and open the software updater and let it run, it'll reload the package lists with the newly configured settings.


Now a caveat, the ppa entries will be listed, but I'm not sure about the cdrom entries.
In case the cdrom entries are not in the Other Software Listing, you might need to manually remove them from tyhe sources.list entry.
To do so, you need to open a text editor as root.
either try 
```
sudo nano /etc/apt/sources.list
```
or
```
gksu gedit /etc/apt/sources/list
```
(I do not think gksu installed by default anymore, so you would need to install it, if you would rather use a non-terminal text editor.
(nano is a terminal-based text editor, it's faster, but the controls may confuse...)

When that is open find the entry line for cdrom they would look something like this
```
deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Alpha amd64 (20140115)]/ trusty main restricted
```
to disable it add a # symbol to the front of the line, like so
```
#deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Alpha amd64 (20140115)]/ trusty main restricted
```
Do this for any entry that starts with cdrom
, and note your's will not be for trusty alpha, it should say precise.
(Also note the cdrom entries are normally listed at the very top of the page)
Then save and close.
(In nano to save and close press ctrl + X, then press y then enter; the y tells the system to save the changes, then the file name will come up and simply pressing enter will save it as the same file name as was when it opened. Do not press anything but enter or else you might change the filename)

Then re-run the updater, like above.

I believe the top part should be all you need to do, and hopefully you can avoid doing the bottom part of manually editing the sources.list file.
Hope this helps.
Or at least makes sense...

Edit: And ninja'd. I am slow today.  .  .

---

### Post by hebdave on 2014-11-27
Thanks to the Moderator for sorting my code out for me, I used the quotes not the code. I found you can use the graphic in advanced posting that says code and then press it twice and stick the code in the middle of the two. Don't know for sure but thats what I will do next time. I assume the code refers to the terminal code that you pop in between.

Also thanks so much for you time and patience sorting me out. I unticked the CD roms which were there and then found even more ppa that said disabled and not supported in upgrade. They were ticked next to the disabled so I thought the tick **had** disabled them. Its the other way round with that though I guess. I did see them before even writing the post in the first place but thought they looked correct. I am not sure were it leaves me with gimp but assume is can be used with out updates until that get sent through to 14.04. I don't use it really yet anyway.

Thanks for you help I just have to restart my computer and it should take effect. Much appreciated !

---

