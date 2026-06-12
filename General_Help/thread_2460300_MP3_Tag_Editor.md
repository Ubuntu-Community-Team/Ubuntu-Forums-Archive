---
title: "MP3 Tag Editor"
date: 2021-04-06
forum: General Help
---

### Post by Paul_Alexander on 2021-04-06
[RESOLVED - see below]

I can't believe I cannot find a solution so I am seeking help from the masses. I've upgraded to 20.04 a few months back and finally need an MP3 tag editor. Specifically, I'm on 20.04.2 LTS on 64bit. Upon upgrading from 18.04, it removed EasyTag which I've used for years - good tool. However, it will not install on 20.04. I've also found that Puddletag cannot navigate to my internal hard drives - it can only reach the / mount so that's no good. Finetune does not install. Kid3 does not install. MusicBrainz Picard will install but will not run. And I don't see any other options in the Software Center. Odd.

---

### Post by daniewicz on 2021-04-06
Are you using the synaptic package manager or snaps?

---

### Post by Brent_Santin on 2021-04-06
Hi, I just upgraded from Lubuntu 18.04 to 20.04 and also found Puddletag (the snap installation version) won't access my secondary drive with all my music on it. Too bad, as I think the layout (spreadsheet style) of Puddletag is very intuitive and useful (seeing the tags of multiple files at once). I hope a non-snap version comes out soon.

I tried Easytag, but when saving the tag changes it gives me some wierd disk access error message, so that one got uninstalled.

I'm now trying Kid3-qt, which is a little like Easytag in its layout. Seems pretty powerful. I just don't love the interface where you select multiple files in a directory, but can only see the tags for one at a time. I'm going to stick with kid3-qt for now. Once I get used to the  "reverse" (from Puddletag) way of doing things, it seems to have a good  array of features. Watching Youtube videos on how to use it was more  helpful than reading the manual.

I too was pretty surprised at the lack of choice for taggers in Linux. Not including Puddletag, they are either really power, but have a cryptic interfaces that take a lot of learning, or have have an overload of features that are unnecessary to me. I just want something easy to use, with an intuitive and elegant interface that does the basics (tagging and adding of images).

---

### Post by daniewicz on 2021-04-06
I successfully installed easytag on ubuntu 20.04 using the synaptic package manager.

---

### Post by DuckHook on 2021-04-06
> **Paul_Alexander said:**
> …Upon upgrading from 18.04, it removed EasyTag which I've used for years - good tool. However, it will not install on 20.04.
:-s
I am on 20.04 and have Easytag installed and running without a hitch. Apt shows that it is available in the repos. Make sure you have Universe turned on:```
duckhook@Zeus:~$  apt show easytag
Package: easytag
Version: 2.4.3-4build1
Priority: optional
Section: universe/sound
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,442 kB
Depends: dconf-gsettings-backend | gsettings-backend, libc6 (>= 2.14), libflac8 (>= 1.3.0), libgcc-s1 (>= 3.0), libgdk-pixbuf2.0-0 (>= 2.30.1), libglib2.0-0 (>= 2.38), libgtk-3-0 (>= 3.10), libid3-3.8.3v5, libid3tag0 (>= 0.15.1b), libogg0 (>= 1.0rc3), libopus0 (>= 1.1), libopusfile0 (>= 0.5), libspeex1 (>= 1.2~beta3-1), libstdc++6 (>= 5), libtag1v5 (>= 1.9.1-2.2~), libvorbis0a (>= 1.1.2), libvorbisfile3 (>= 1.1.2), libwavpack1 (>= 4.40.0)
Recommends: gnome-icon-theme, gvfs, yelp
Suggests: easytag-nautilus
Homepage: https://wiki.gnome.org/Apps/EasyTAG
Download-Size: 727 kB
APT-Manual-Installed: yes
APT-Sources: http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: GTK+ editor for audio file tags
 EasyTAG is an utility for viewing, editing and writing
 the tags of different audio files, using a GTK+ interface.
 .
 Currently EasyTAG supports the following:
  - View, edit, write tags of MP3, MP2 files (ID3 tag), FLAC files (FLAC Vorbis
    tag), Ogg Opus, Ogg Speex and Ogg Vorbis files (Ogg Vorbis tag),
    MP4/M4A/AAC files (MPEG-4 Part 10 tag), and MusePack, Monkey's Audio files
    (APE tag);
  - Auto tagging: parse file and directory names using masks to automatically
    fill in tag fields;
  - Cover art support for all formats;
  - Rename files from the tag fields (using masks) or by loading a text file;
  - Process selected files of the selected directory;
  - Ability to browse subdirectories;
  - Recursion for tagging, removing, renaming, saving, etc;
  - Can set a field (artist, title, ...) on all other selected files;
  - Read file header information (bitrate, time, ...) and display it;
  - Undo and redo last changes;
  - Ability to process tag fields and file names (convert letters into
    uppercase, lowercase, etc);
  - Ability to open a directory or a file with an external program;
  - CDDB support (from http protocol);
  - A tree based browser;
  - A list to select files;
  - A playlist generator window;
  - A file searching window;
  - Simple and explicit interface.
```

When attempting to install, did you remember to first do?:```
sudo apt update
```

Please try to install using apt and post all output back to this thread:```
sudo apt install easytag
```
> **Brent_Santin said:**
> Hi, I just upgraded from Lubuntu 18.04 to 20.04 and also found Puddletag (the snap installation version) won't access my secondary drive with all my music on it. Too bad, as I think the layout (spreadsheet style) of Puddletag is very intuitive and useful (seeing the tags of multiple files at once). I hope a non-snap version comes out soon.
This is likely a result of Puddletag not having permissions turned on to allow "Read/write files on Removable Storage Devices". This is a common problem with snaps and the description is also misleading. The switch has to be turned on to access any partition outside of /home. Instructions for turning on this option: [https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)
> **daniewicz said:**
> I successfully installed easytag on ubuntu 20.04 using the synaptic package manager.
When trying to triage, it's best to stick with the command line because doing so will display error outputs. Neither Synaptic nor Software Centre provide any usable feedback.

---

### Post by cscj01 on 2021-04-08
I have been using Puddletag for years. They have moved it to snap, but my install on 20.04 after my upgrade from 18.04 works as always. I keep my music on a separate drive and have no issues accessing it.  What message do you get when you try to access you music drive?

---

### Post by Paul_Alexander on 2021-04-08
To he who asked, the puddletag app simply has no navigation below /media so it's dead to me.

To others, thanks a bunch! I will try some of these options later today. Sure appreciate it, all;-).

---

### Post by Paul_Alexander on 2021-04-08
Hmmm, I see @duckhook may have unblocked me. I'll check into this first.

I'm not receiving any email notifications from this site anymore, it seems, so I need to repair this as well since I didn't see any replies until going directly here...

---

### Post by DuckHook on 2021-04-08
> **Paul_Alexander said:**
> …I'm not receiving any email notifications from this site anymore, it seems, so I need to repair this as well since I didn't see any replies until going directly here...
Sadly, the e-mail notifications have not been reliable for some time. Since forum staff do not maintain the HW/SW of the forums (we administer only the content within), we must patiently wait for our ticket to get addressed by the sysadmins. The problem is not at your end and I'm afraid there isn't anything you can do except revisit your thread every so often.

---

### Post by Paul_Alexander on 2021-04-08
Thank you, Duckhook. Good job and good to know. Here's what I did to fix it. Getting it through this source properly exposes files from my internal hard drives.

*-- add the universe repo*
```
sudo add-apt-repository universe
```

*--update my package list*
```
sudo apt-get update
```

*--get it*
```
sudo apt install easytag
```

---

### Post by DuckHook on 2021-04-08
Glad you solved it. I've marked you thread "Solved", which you can find within the Thread Tools menu in your first post.

---

### Post by daniewicz on 2021-04-09
Another snap failure. :mad:

---

### Post by DuckHook on 2021-04-09
> **daniewicz said:**
> Another snap failure. :mad:
I feel your pain, but in this case, it is the way that snaps were properly designed to behave. Part of snapcraft's function is to jail apps to prohibit them from running rampant on the rest of your system. So, a nasty app might have access to certain files on your /home, but it can't act on your NFS shares. Security in depth: in this case, layers. Higher security is the default. You have to make a conscious act to lower it and give it unfettered access.

The problem is not the principle involved (which is a good one) but the lack of clarity. Before snaps are installed, they should come with a warning as well as jailbreaking instructions.

---

### Post by daniewicz on 2021-04-09
Interesting.

Thanks for this.

---

### Post by CelticWarrior on 2021-04-10
> [COLOR=#000000]The problem is not the principle involved (which is a good one) but the lack of clarity. Before snaps are installed, they should come with a warning as well as jailbreaking instructions.[/COLOR]
When we understand that snaps are to be installed via the software store and that right after installation there's a huge red Permission button, everything should be self-explanatory after clicking it.

---

