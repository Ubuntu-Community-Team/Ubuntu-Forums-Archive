---
title: "Firefox and downloads"
date: 2012-11-03
forum: General Help
---

### Post by offgridguy on 2012-11-03
I use firefox as my browser, both for ubuntu and windows7,  I like firefox, but I seem to
have a lot of issues with downloads,  either it won't download or more often  won't
install.  Has anyone experienced similar difficulties?  :confused:

---

### Post by Frogs Hair on 2012-11-03
I haven't had this problem. Is this a Firefox problem in both Windows and Ubuntu and have tested with other browsers ?

What kinds of packages are you trying to install in Ubuntu and are they Linux compatible ?

---

### Post by offgridguy on 2012-11-03
> **Frogs Hair said:**
> I haven't had this problem. Is this a Firefox problem in both Windows and Ubuntu and have tested with other browsers ?

What kinds of packages are you trying to install in Ubuntu and are they Linux compatible ?

Thank you for the reply.  I haven't encountered this problem with
firefox in windows.
   I haven't tried any other browser yet,  overall I like firefox 
and am reluctant to change I guess.
   An example of what I am trying to download, Cheese webcam,
This showed up on the launcher saying awaiting install, never got past that point.
  Another example Imagemagic, this time failed to download, no
indication of progress or completion.
    Some times it works flawlessly,eg. gparted.    By the way, what is a padawan?

---

### Post by SeijiSensei on 2012-11-03
> **offgridguy said:**
>    An example of what I am trying to download, Cheese webcam,

I suspect your rather new to Linux.  In 99.99% of the cases where you need to install software you should be using the Add/Remove software applicationor the Software Center within Ubuntu.  All software for Ubuntu is maintained in "repositories" for each release and is tested for compatibility.  The only time you might want to download an application directly from a developer's site is if there is a new release that includes needed features not yet included in the official version in the repositories.

The other option is to install from the command prompt.  If you open the Terminal application and type "sudo apt-get install cheese" it will set it up for you.

I suggest you read [this document](https://help.ubuntu.com/community/Repositories/Ubuntu) on how repositories work.

> By the way, what is a padawan?

It's a term from the Star Wars movies meaning "apprentice."

---

### Post by offgridguy on 2012-11-03
Thank you for the reply, actually in the example of cheese webcam i did use the add, remove feature in the software center.
In the case of Imagemagic, I used the command line, no luck there either.
     And yes i am new to linux, I have been using 12.04 now for 4 months only.   Other than software, I download interesting articles, or music lead
sheets from wikifonia. Pictures in email and occasionally other types of
document data.  :)

I have just tried reinstalling cheese, this time without a hitch. Yeah

---

### Post by offgridguy on 2012-11-03
An update here, I have just installed digikam from the software center, again without a hitch.  one difference of note is that I am using the wifi
network at the public library.  This is mainly on account of $$$$ as my ISP
gives me 500mb for$40 every 500mb after is another $10,monthly rate, but it adds up fast, I have just updated 12.04 approx 480 mb, this update went well.  :)

This may be more of network issue than anything, the library network is no faster than my
own private network but it may be better.

---

### Post by oldos2er on 2012-11-03
> **offgridguy said:**
>   Another example Imagemagic, this time failed to download, no
indication of progress or completion.

Make sure you're using the correct package name: ```
sudo apt-get update && sudo apt-get install imagemagick
```

Or search for "imagemagick" in Software Center.

---

### Post by offgridguy on 2012-11-03
Thank you oldos2er.

Don't know what I'm missing here, I pasted this in the terminal ,it looked like things
were happening but no dice.
> 
sudo apt-get update && sudo apt-get install imagemagick

---

### Post by offgridguy on 2012-11-03
digiKam installed okay but it doesn't work any better than it ever did, it will be uninstalled shortly.

---

### Post by oldos2er on 2012-11-04
> **offgridguy said:**
> Thank you oldos2er.

Don't know what I'm missing here, I pasted this in the terminal ,it looked like things
were happening but no dice.

I'd need to see all the terminal output from that command, if you could copy & paste it here.

---

### Post by offgridguy on 2012-11-04
> **oldos2er said:**
> I'd need to see all the terminal output from that command, if you could copy & paste it here.

-Aspire-5735:~$ sudo apt-get && sudo apt-get install imagemagick
[sudo] password for 
apt 0.8.16~exp12ubuntu10.5 for i386 compiled on Oct 15 2012 09:56:17
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
imagemagick is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans graphicsmagick kde-l10n-de libbluray1
  language-pack-kde-de language-pack-kde-en libsvga1 language-pack-de-base
  language-pack-kde-zh-hans esound-common language-pack-kde-en-base
  kde-l10n-engb language-pack-kde-de-base kde-l10n-zhcn libesd0 libaacs0
  libaudiofile1 firefox-locale-de libvdpau1 language-pack-zh-hans-base
  firefox-locale-zh-hans language-pack-de libgraphicsmagick3
  language-pack-kde-zh-hans-base libmpeg2-4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Aspire-5735:~$ ^C
-Aspire-5735:~$ ^C-Aspire-5735:~$ 

Here you are, and thank you for replying.

---

### Post by oldos2er on 2012-11-04
> **offgridguy said:**
> -Aspire-5735:~$ sudo apt-get && sudo apt-get install imagemagick

That should've been sudo apt-get *update* && sudo apt-get install imagemagick, but no matter because > **offgridguy said:**
> 
imagemagick is already the newest version. So you've already got it. If you need help, ```
man imagemagick
```

---

### Post by offgridguy on 2012-11-04
Thank you, this explains why i couldn't find it.

---

### Post by oldos2er on 2012-11-04
I don't use Unity, but I think if you install a CLI app you need to run it in a terminal because Unity's launcher won't find it. Maybe some Unity user could correct me if I'm wrong....

---

### Post by offgridguy on 2012-11-04
I honestly don't know either,my experience using the terminal is very limited,   but would it show up in
apps. on another DE ?

---

### Post by SeijiSensei on 2012-11-04
Imagemagick is a set of command-line programs.  As far as I know the standard package has no GUI.

Most of the time the "convert" program is the key.  As a simple example, here's the command to shrink a graphic by 50% and convert it from a PNG to a JPEG:

```
convert file.png -resize '50%' file.jpg
```

Convert is an incredibly powerful program, but you should read the [documentation]("http://www.imagemagick.org/script/convert.php") to get a sense of how it works.

If you just need to do simple things like crop and resize images, most any graphics editor like GIMP will do that.  I often use gwenview which is primarily a graphics browser but has some additional functionality like cropping and scaling images.  Adding the kipi-plugins package gives it a lot more power.

As a command-line program, convert is handy if you need to transform an entire set of images.  With a bit of scripting, you can do some [nifty things]("http://ubuntuforums.org/showthread.php?t=1951949").

---

### Post by offgridguy on 2012-11-04
Thank you for the info.

---

