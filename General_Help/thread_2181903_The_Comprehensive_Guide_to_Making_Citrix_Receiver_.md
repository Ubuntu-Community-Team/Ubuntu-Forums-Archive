---
title: "The Comprehensive Guide to Making Citrix Receiver work on Kubuntu 13.10"
date: 2013-10-19
forum: General Help
---

### Post by the_king_of_nerds1310 on 2013-10-19
This is how I made Citrix Receiver work on the new Kubuntu 13.10.

Be forewarned, this is a long post.  Read only if you are curious about *the whole process*.

(On the bright side, you will end up with a reusable .deb installation file for Citrix Receiver.)

[FONT=arial black]==================[/FONT]
[FONT=arial black]Prerequisite steps[/FONT]
[FONT=arial black]==================[/FONT]

Remove any previously installed ICA client.

```
sudo dpkg -P icaclient
```

We need the apt-file tool, so go ahead and install that.

```
sudo apt-get -y install apt-file
sudo apt-file update --architecture i386
sudo apt-file update --architecture amd64
```

[FONT=arial black]========================[/FONT]
[FONT=arial black]Extracting the ICA files[/FONT]
[FONT=arial black]========================[/FONT]

First, we unpack the ICA package instead of installing it:

```
dpkg-deb -x icaclient_12.1.0_amd64.deb foo
```

Unpacking gets around a couple of bugs in the ICA package, which we will fix later.

[FONT=arial black]=======================================================
List all DEB dependencies / packages used by ICA Client
=======================================================
[/FONT]
Next, we run some useful commands to pull dependency information out of the unpacked ICA files.

List all ICA binaries:

```
find foo/opt/Citrix/ICAClient/ -exec file {} ';' | grep "ELF" | grep "executable" > ica_elf_list
```

List all libraries linked by those:

```
cat ica_elf_list | while read f; do arch=$(echo "$f" | grep -o '..-bit' | sed 's/32-bit/i386/' | sed 's/64-bit/amd64/'); file=$(echo "$f" | awk '{print $1}' | sed 's/://g'); ldd "$file" | sed "s/^/$arch/g"; done | sort | uniq > ica_so_list
```

List all currently satisfied DEB packages dependencies:

```
cat ica_so_list | awk '{print $4}' | grep '^/' | sort | uniq | while read f; do dpkg -S "$f"; done > ica_deb_list
```

Remove duplicate entries for DEB packages that provide more than one library:

```
cat ica_deb_list | awk '{print $1}' | sed 's/:$//g' | sort | uniq > ica_deb_list_final
```

[FONT=arial black]=========================================================
List all missing .so / library files needed by ICA Client
=========================================================
[/FONT]
Finally, we can figure out which libraries we are missing:

```
cat ica_so_list | grep "not found" > ica_so_missing
```

[FONT=arial black]=================================
Making a working ICA installation
=================================
[/FONT]
Next, we use use apt-file to find missing packages that provide the libs listed in ica_so_missing, like this:

```
cat ica_so_missing | while read f; do arch=$(echo "$f" | awk '{print $1}'); file=$(echo "$f" | awk '{print $2}'); apt-file find -x "$file$" -a $arch | sed "s/: /:$arch provides /g"; done > ica_missing_packages
```

Next, we prune out dependencies that are provided by multiple packages:

```
cat ica_missing_packages | awk '{print $3}' | sort | uniq | while read provided; do providers=$(grep "provides $provided" ica_missing_packages | awk '{print $1}'); count=$(echo $providers | wc -w); selected=$providers; if [ $count -gt 1 ]; then echo "Multiple packages can provide $provided, please select one:" >&2; select selected in $providers; do break; done < /dev/tty; echo "You selected $selected" >&2; fi; echo $selected; done > ica_selected_packages
```

(If you're asked to choose between libasound2:i386 and liboss4-salsa-asound2:i386, the right choice on most Ubuntu installations is the first one.)

Next, we install the missing packages.

```
missing=$(cat ica_selected_packages | awk '{print $1}'); sudo apt-get -y install $missing
```

Finally, we recreate the lists of available and missing libs and packages (same commands as before):

```
cat ica_elf_list | while read f; do arch=$(echo "$f" | grep -o '..-bit' | sed 's/32-bit/i386/' | sed 's/64-bit/amd64/'); file=$(echo "$f" | awk '{print $1}' | sed 's/://g'); ldd "$file" | sed "s/^/$arch/g"; done | sort | uniq > ica_so_list
cat ica_so_list | awk '{print $4}' | grep '^/' | sort | uniq | while read f; do dpkg -S "$f"; done > ica_deb_list
cat ica_deb_list | awk '{print $1}' | sed 's/:$//g' | sort | uniq > ica_deb_list_final
cat ica_so_list | grep "not found" > ica_so_missing
cat ica_so_missing | while read f; do arch=$(echo "$f" | awk '{print $1}'); file=$(echo "$f" | awk '{print $2}'); apt-file find -x "$file$" -a $arch | sed "s/: /:$arch provides /g"; done > ica_missing_packages
```

Please make sure that the "ica_so_missing" file is now empty, meaning there are no more dependencies to satisfy.

[FONT=arial black]====================================
Creating a minimal Dependencies list
====================================
[/FONT]
There are probably a lot of redundant entries in the list of prerequisite DEB packages, since there are likely lots of inter-dependencies between the packages.

I think it is comme il faut to minimize the list of dependencies when creating a package such that any dependency that happens to (currently) already be included by another dependency is not explicitly listed.

Therefore, we first figure out all sub-dependencies of our current (long) list of dependent packages:

```
checked=""; unnecessary=""; unchecked="$(cat ica_deb_list_final) EOF"; while read -d ' ' f <<< $unchecked; do checked="$f $checked"; candidates=$(apt-cache depends "$f" | grep '\sDepends' | awk '{print $2}' | sed 's/[<>]//g'); unchecked="$(for d in $candidates; do if ! grep -q $d <<< $checked; then echo -n "$d "; fi; done) $unchecked"; unchecked="$(echo $unchecked | sed "s/$f //g")"; unnecessary="$(for d in $candidates; do if ! grep -q $d <<< $unnecessary; then echo -n "$d "; fi; done) $unnecessary"; done; for u in $unnecessary; do echo "$u"; done > ica_implicit_dependencies
```

Next, we figure out which of our original dependencies is not in that list:

```
original=$(cat ica_deb_list_final); for f in $original; do if ! grep -q $f ica_implicit_dependencies; then echo "$f"; fi; done > ica_explicit_dependencies
```

And that way we get the final, correct list of dependencies, which on my OS/arch/version happens to look like this:

libasound2:i386
libc6:amd64
libffi6:amd64
libglib2.0-0:amd64
libgstreamer0.10-0:amd64
libgstreamer-plugins-base0.10-0:amd64
libgstreamer-plugins-base0.10-0:i386
libgtk2.0-0:i386
liblzma5:amd64
libpcre3:amd64
libstdc++6:i386
libxaw7:i386
libxm4:i386
libxml2:amd64
libxp6:i386
zlib1g:amd64

In addition to these, "nspluginwrapper" is also a good idea to install, even though it is not explicitly needed by the ICA software, it is necessary for integration with some browsers.

Whether to add nspluginwrapper as a Suggests or Depends entry in the DEBIAN/config file is a matter of taste and standards, I suppose.  We'll get to that later.

[FONT=arial black]=======================================
Modifying the broken Citrix DEB package
=======================================
[/FONT]
The original Citrix Receiver DEB package will confuse the APT system in two ways.

(a) It has a bunch of wrong Dependencies in it's control file.  As has been described elsewhere, the fix is to remove the faulty dependencies from DEBIAN/control and rebuild the deb.

(b) There's a post-installation script in the package that fails on AMD64 platforms.  As has been described elsewhere, the fix is to patch that script and rebuild the deb.

First, let's fix the script that fails.

Extract the DEB control scripts, and replace the faulty grep command with one that works on AMD64 as well as i386:

```
dpkg-deb --control icaclient_12.1.0_amd64.deb foo/DEBIAN
sed -i 's/grep "i\[0-9\]86"/grep "i\\?[x0-9]86"/g' foo/DEBIAN/postinst
```

Next, let's put in the proper dependencies for our operating system and version:

```
new_depends="$(cat ica_explicit_dependencies | tr '\n' ',') nspluginwrapper"; sed -i "s/^Depends: .*$/Depends: $new_depends/" foo/DEBIAN/control
```

[FONT=arial black]==================================================
Fixing the CA keystore (optional, but recommended)
==================================================
[/FONT]
The list of CA root certificates shipped with the Citrix Receiver for Linux is horribly outdated.

To fix this, we can simply link the keystore in the ICA client with the system's CA keystore, like this:

```
rm -rf foo/opt/Citrix/ICAClient/keystore/cacerts
ln -s /etc/ssl/certs foo/opt/Citrix/ICAClient/keystore/cacerts
```

[FONT=arial black]=================================================================================
Automatically opening .ica files with Citrix Receiver (optional, but recommended)
=================================================================================
[/FONT]
In order for browsers and desktop icons to automatically launch Citrix Receiver when an .ica file is clicked, we need a bit of glue to integrate things.

Let's add that.

```
mkdir -p foo/usr/share/applications
printf '[Desktop Entry]\nName=Citrix ICA client\nComment="Launch Citrix applications from .ica files"\nCategories=Network;\nExec=/opt/Citrix/ICAClient/wfica\nTerminal=false\nType=Application\nNoDisplay=true\nMimeType=application/x-ica' > foo/usr/share/applications/wfica.desktop
```

[FONT=arial black]=============================
Building a working Citrix DEB
=============================
[/FONT]
Let's go ahead and wrap up the result in a DEB installer, so that we can reuse it in the future rather than going through this lengthy guide:

```
dpkg -b foo icaclient_12.1.0_amd64_fixed_for_kubuntu13.10.deb
```

[FONT=arial black]=============================
Installing the new Citrix DEB
=============================
[/FONT]
Let's go ahead and install the finished product.

```
sudo dpkg -i icaclient_12.1.0_amd64_fixed_for_kubuntu13.10.deb 
```

Click Yes on the EULA to dismiss it, and the package should install without errors.

Clicking an .ica link in a browser should now automatically launch wfica and thus open a remote app or desktop.

You're done - happy Citrixing!

[FONT=arial black]==============================
Final note regarding upgrading
==============================
[/FONT]
I also tried the Customer Preview, aka Citrix Receiver version 12.9.999 (build 244295) released on 2013-july-15.

It crashes with SIGSEGV every time I run it on Kubuntu 13.10.

YMMV, my recommendation is to try this guide with the stable version before you attempt to use the beta.

---

### Post by the_king_of_nerds1310 on 2013-10-19
I tried to upload the finished .deb file, but got an error message from the Ubuntu forum software about the image being too large.

Oh well, maybe someone else who knows how to attach files to posts can upload it...

---

### Post by vanadium on 2013-10-19
The citrix nightmare. Unfortunately, we need this crap, but getting it to work is increasingly difficult with each version of Ubuntu. Your guide is for Kubuntu. I tried it on Ubuntu and it went wrong here:
```

$ cat ica_so_missing | while read f; do arch=$(echo "$f" | awk '{print $1}'); file=$(echo "$f" | awk '{print $2}'); apt-file find -x "$file$" -a $arch | sed "s/: /:$arch provides /g"; done > ica_missing_packages
ftack@vanadium:~/Downloads$ missing=$(cat ica_missing_packages | awk '{print $1}'); sudo apt-get -y install $missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 liboss4-salsa-asound2:i386 : Conflicts: libasound2:i386
E: Unable to correct problems, you have held broken packages.

```

I continued the procedure until the check where no dependencies would anymore be missing:

```

$ cat ica_so_missing 
i386	libasound.so.2 => not found
i386	libgstapp-0.10.so.0 => not found
i386	libgstinterfaces-0.10.so.0 => not found
i386	libgstreamer-0.10.so.0 => not found
i386	libstdc++.so.6 => not found
i386	libXaw.so.7 => not found
i386	libXpm.so.4 => not found
i386	libXp.so.6 => not found

```

I got it working with the procedure outlined here: [http://ubuntuforums.org/showthread.php?t=2166020&p=12816007#post12816007](http://ubuntuforums.org/showthread.php?t=2166020&p=12816007#post12816007). I first tried with the "stable" icaclient_12.1.0_amd64.deb. While installation succeeded without error, it would not run because on run time, the wfica program would still require libasound.so.2 (I found this out trying to start wfica.sh from the command line, providing a link to an application on a citrix server). It worked, though with the beta version, icaclient_12.9.999.244295_amd64.deb.

```

ICACLIENT=icaclient_12.9.999.244295_amd64.deb
mkdir ica_temp ; dpkg-deb -x $ICACLIENT ica_temp ; dpkg-deb --control $ICACLIENT ica_temp/DEBIAN ; sudo gedit ica_temp/DEBIAN/control

```
(code to run in the directory where the icaclient file was downloaded)

Change the dependencies to be "Depends: libc6-i386 (>= 2.7-1), lib32z1, nspluginwrapper"

Save and close the file

Compile and install the deb file
```

dpkg -b ica_temp icaclient-modified.deb 
sudo dpkg -i icaclient-modified.deb

```

Cleanup with
```

rm -r ica_temp

```

In addition, I had to make the firefox certificates available for citrix:
```

sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/

```

---

### Post by cariboo on 2013-10-19
Moved to general Help, as Saucy has been released.

---

### Post by zombienerd1 on 2013-10-24
I can't thank you enough for your post.  This worked perfectly for me in Ubuntu 13.10 64 bit.  I did  [COLOR=#333333][FONT=UbuntuMono]sudo apt-get install libmotif4:i386 nspluginwrapper  [/FONT][/COLOR]Before I began your instructions.

---

### Post by echidna99 on 2013-11-01
I followed the instructions exactly and this worked for me.
What a mess, lets hope citrix can sort themselves out soon.
Thanks for providing this guide.

---

### Post by vanadium on 2013-11-01
Did not work for me, but I see that others had more luck. I might try again later, but I will stick with the beta version for now.

---

### Post by jorge.guerrero.d on 2013-11-06
Great!, this solution works perfect!

---

### Post by volkerbradley on 2013-11-12
Works perfectly for me as well.
Thank you.

---

### Post by xappadres on 2013-11-21
Hello [**[COLOR=#000000]the_king_of_nerds1310[/COLOR]**]("http://ubuntuforums.org/member.php?u=1872442"), many thanks for posting this solution. It worked for me after a lot of trying several alternatives that didn't do the job.

Thanks again!

---

### Post by ftj-guillemot on 2013-11-23
Works perfectly on Ubuntu 13.10 with the latest icaclient 13 64bits.
Thanks.

---

### Post by vanadium on 2013-11-24
Indeed, it appears that now a new version was released. I am running with the beta currently. It is not perfect: sometimes a connection fails, but overall, it works. I am not sure if I am going to try the definitive version now ...

---

### Post by vanadium on 2013-11-24
Yes, it worked! You still need to edit the dependencies, though. I again followed the (short) procedure I already indicated in [my previous post](http://ubuntuforums.org/showthread.php?t=2181903&p=12821080#post12821080), which involves unpacking the file, removing two dependencies, and recompiling the deb file before installing it.

---

### Post by the_king_of_nerds1310 on 2013-12-02
Hi guys

Thanks for the feedback!

Very happy that it worked for most people.

(Also, amazed that anyone managed to find this solution, plus work all the way through it. ;-))

Take care

---

### Post by the_king_of_nerds1310 on 2013-12-02
NB.

I managed to partially solve one additional issue, where part of the wfica window "hides" beneath the taskbar when it is run in fullscreen mode.

Not sure if this is only an issue with Kubuntu/KDE/plasma, or if it also exists in vanilla Ubuntu..

[B]UPDATE: This is only an issue in Citrix Receiver version 12.1.  The newly released Citrix Receiver for Linux version 13.0 does not have this issue, it stays nicely within the desktop viewport.
[/B]
Either way; my partial solution is as follows.

1) We need the wmctrl application, make sure it is installed:

```
$ sudo apt-get install wmctrl
```

2) First, get the size of the current desktop viewport:

```
$ viewport=$(wmctrl -d | grep '*' | grep -Po 'WA:\s*\d+,\d+\s+\d+x\d+' | awk '{print $3}')
```

3) Next, split it into width and height:

```
$ IFS=x read -r width height <<< "$viewport"
```

4) wfica goes into a windowed mode when we give it a fixed geometry, meaning that it has a titlebar.  Subtract the size of that titlebar, with my window manager it is about 20 pixels:

```
$ let height-=20
```

5) Finally, append the result to /etc/environment:

```
$ sudo sed -i '$ a\export WFICA_OPTS="-geometry '${width}x${height}'+0+0"' /etc/environment
```

Now, you should have a line like this at the bottom of /etc/environment:

```
export WFICA_OPTS="-geometry 1266x701+0+0"
```

With the numbers matching your current desktop viewport.

To apply the change, reboot computer.

To revert the change, remove the offending line in /etc/environment and reboot.

I haven't found a clever / pretty way to integrate this into the .deb package (yet).

It is only a partial solution; by which I mean that while fullscreen Citrix apps stop hiding beneath the taskbar, this solution also causes windowed apps to maximize and take up the entire desktop area, which is a bit visually unappealing.

Anyway, if wfica is hiding beneath your taskbar, there you go :-)

BR

---

### Post by the_king_of_nerds1310 on 2013-12-02
Hi
> **vanadium said:**
> I tried it on Ubuntu and it went wrong here:```

The following packages have unmet dependencies:
 liboss4-salsa-asound2:i386 : Conflicts: libasound2:i386

```

Oops.  You have a dependency, which can be satisfied by several packages.

The solution I posted tries to satisfy it by installating both; an attempt which is immediately aborted, because the two packages happen to be conflicting.

I've updated the solution to include an additional step, where alternative dependencies are pruned by asking the user which one to use.

Please try again?

BR

---

### Post by konradsa on 2014-02-01
Holy ****, thank you so much for your guide, would have never figured this out myself. This also work on 14.04, in case anybody is wondering.

I am also wondering why it seems to be getting more difficult to install the Citrix client with every new Ubuntu version. This should just be a simple thing, but no, it's hell. As long as stuff like that is not as easy as under Windows, Linux will not be able to compete on the desktop. But I guess only Citrix is to blame here.

One suggestion I have to improve the original post: Pleae put empty lines between the commands if they are separate. When it's wrapping over, it's hard to tell what is a new command or what just wrapped around to another line. This may be a challenge especially for novices, it won't work for them and they give up.

---

### Post by paranjr on 2014-05-02
I tried this very comprehensive guide.  I can connect to the citrix remote site I need; but none of the icons or apps work.  They seem like something is happening, but nothing does.  I have a 64 bit AMD processor, am running ubuntu 14.04.  I will appreciate any help you can give me to help fix this issue.  My machine dual boots windows 8.  On windows side, same url works great and all apps work at the web site.  Thanks

---

### Post by whorush on 2014-06-14
thanks so much, just got it installed!  believe it or not, i switched to windows 2 years ago to run citirx.  thinking about coming back now.

strange thing.  my company "upgraded" their server side now, and now "my computer" opens in the browser tab that i launch it in, either chrome or firefox.  i'd much rather it be in it's own window so that alt-tab could pass through and so that i could expand it to two monitors and whatnot.  any ideas?  thanks!!!!

---

### Post by Alexisnf on 2014-09-11
Thanks so much !!, this guide solved hours of investigation, and finally is working in my Notebook. I've installed Ubuntu Gnome 14.04 32bit, and followed instructions to install Citrix icaclient_13.0.0.256735_i386.deb. It's working with Chromium.
I'm totally newbie on Linux, and I am trying to change from Windows to Linux. This allow me to stay connected to my company.


Thanks

---

### Post by leilamoniz on 2014-11-05
hi all,

currently running ubuntu 14.04 LTS and following instrucions up until i came accross error below:

```
Ignoring source without Contents File:
  http://archive.canonical.com/ubuntu/dists/trusty/Contents-amd64.gz
Ignoring source without Contents File:
  http://extras.ubuntu.com/ubuntu/dists/trusty/Contents-amd64.gz
Ignoring source without Contents File:
  http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/trusty/Contents-amd64.gz
Ignoring source without Contents File:
  http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/trusty/Contents-amd64.gz
root@acer-Aspire-5920:~# dpkg-deb -x icaclient_12.1.0_amd64.deb foo
dpkg-deb: error: failed to read archive `icaclient_12.1.0_amd64.deb': No such file or directory
root@acer-Aspire-5920:~# dpkg-deb -x icaclient_12.1.0_amd64.deb foo
dpkg-deb: error: failed to read archive `icaclient_12.1.0_amd64.deb': No such file or directory
```

im very new to all OS functions, i understand this post backdates 1 year back, and it seems there has been changes in the way of installing ftj-guillemot post:

```
ftj-guillemot -November 23rd, 2013-                   [INDENT]                              Re: The Comprehensive Guide to Making Citrix Receiver work on Kubuntu 13.10
                          Works perfectly on Ubuntu 13.10 with the latest icaclient 13 64bits.
Thanks.         [/INDENT]
    

```

can sum1 plz advice what the commands should be for ubuntu 14.04 LTS 64bit ... thx in advance

---

### Post by King of Heart 4711 on 2015-03-17
I have the latest Citrix ICA Client running on Ubuntu 14.04 PERFECTLY.. but with once glitch. USB Devices.

we have a requirement at my company that USB Device access needs to work for a few pre-approved devices. This works fine in windows, but is not working on Ubuntu.

I followed the Citrix guide [here]("https://support.citrix.com/proddocs/topic/receiver-linux-13-0/linux-install.html") but issues remain. I've even gone ahead and took the "Ultimate Fallback" approach in $ICAROOT/usb.conf and commented out all the default DENY: rules and only left the default ALLOW: rule but to the same effect.

Has anyone had any experience setting up Citrix ICA Client on Ubuntu (or Linux in general) with USB support??

---

### Post by kelvinator on 2015-05-23
I am using the Chrome browser on Ubuntu 15.04. The Chrome Marketplace has a Citrix Receiver that is very easy to install and use.
In my case all I needed to do was to 
1. Install
2. Start App
3. Enter my employer's URL
4. Login
5. Verify Credentials.

Worked like a charm.

---

### Post by Simon_D._Levy on 2015-07-29
Just wanted to thank the OP for this incredible work.  Thanks to you I have FINALLY been able to install and run a Citrix client on Ubuntu 14.04.

---

