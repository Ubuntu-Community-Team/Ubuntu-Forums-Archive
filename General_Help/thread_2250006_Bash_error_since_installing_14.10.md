---
title: "Bash error since installing 14.10"
date: 2014-10-26
forum: General Help
---

### Post by LaserHosen on 2014-10-26
Hi, Yesterday, I installed utopic unicorn to my old MSI Wind U100 netbook (Lubuntu 14.10). I was using 14.04 with no problems for months. I did a complete wipe and reinstall without updates, since the installer wouldn't find my WiFi network. I decided to install all updates after base installation.

 Before I installed any updates I went to Preferences>Software & Updates and changed the "Download from" setting. 

The default was "Server for United Kingdom" (which has always worked before) and I scanned for a faster UK server before getting my system up to date.  It didn't seem any faster than "Server for United Kingdom" so I changed it back to the default again after installing updates.  

I like to initiate the update manager daily from the terminal by using "sudo update-manager" and entering my sudo password rather than using the GUI.    

Now, when I initiate updates I get this error in bash before update-manager starts:    **** (update-manager:2028): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files**   

Everything still works, but I wonder if I've enabled a repo that's inaccessible or if this is a bug in the new Lubuntu. 

 Any ideas how to fix this annoying message?  Thanks.

---

### Post by sudodus on 2014-10-26
Many GUI application programs issue such warnings and still work. Look out for error messages (but you can live with warnings).

An alternative is to use the 'command line interface' with

```
sudo apt-get update
sudo apt-get dist-upgrade
```

*Edit*: and the following list of related commands (originally posted by *oldfred*) that might be helpful is case of problems

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

---

### Post by LaserHosen on 2014-10-26
Just ran through all those commands **sudodus**, closed command line interface and opened a new one.

I still get the warning message when using "sudo update-manager".

What I have noticed is that the error code changes every time: (**update-manager:2028**) will change to (**update-manager:3091**), for example.

I'm assuming that this is just a new process number being raised each time I initiate an instance of the update-manager.

---

### Post by sudodus on 2014-10-26
Yes, I think it is the process number.

And don't worry about those warnings. I thought that maybe you'd prefer the apt-get commands instead of a GUI tool that issues warnings.

---

### Post by LaserHosen on 2014-10-26
It isn't worrying me. I'm just finding it annoying that nothing like that ever happened in 14.04 and now it suddenly gives me the warning in 14.10.

So, to reiterate: if I want to update my system without using the GUI I can just make a bash script of your post or type in **sudo apt-get update** every day?

---

### Post by sudodus on 2014-10-26
```
sudo apt-get update
``` updates the list of current packages in the repositories
```
sudo apt-get upgrade
``` does the updating (installs the current packages (replacing the old versions))
```
sudo apt-get dist-upgrade
``` does the updating in a more advanced way fixing conflicts if any, and installs kernel packages (if a kernel update is available within the same Ubuntu version)

-o-

```
sudo do-release-upgrade
``` upgrades to the next Ubuntu version, and is something that you should *not* do unless you have backed up your system

-o-

You can make an alias (give it any name you like, just check that it is not a name, that is already used).

```
alias UU='sudo apt-get update && sudo apt-get dist-upgrade'
```

You can store the alias in the file **~/.bashrc** 

Make a new line near the existing aliases in the file. It will be available in all new terminal windows after saving the edit to the file **~/.bashrc**

---

### Post by ajgreeny on 2014-10-26
Actually it should not be ```
**sudo** update-manager
``` as the update manager is a GUI application; it ought to be ```
**gksu** update-manager
```You will have to install gksu before you can use it as it is not installed any more by default and is theoretically becoming slowly deprecated in favour of pkexec, but at present that is much more complicated to use, and as far as I'm aware, will not work with some applications.
As an example, in my Xubuntu 12.04 the only use of pkexec that I have found works for some applications, eg, thunar is ```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY thunar
``` which is more difficult to remember as a command than a simple ```
gksu thunar
```Perhaps over time this will change so a simple **thunar-pkexec** will work.  Or perhaps all this is because the devs prefer us not to use a file manager as root under any circumstances.

---

