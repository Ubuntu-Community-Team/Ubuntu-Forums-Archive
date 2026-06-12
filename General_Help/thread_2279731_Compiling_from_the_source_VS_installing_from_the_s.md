---
title: "Compiling from the source VS installing from the software center?"
date: 2015-05-25
forum: General Help
---

### Post by remmas-sido on 2015-05-25
Hello guys 
Usually Ubuntu Long Term Support releases freeze the package version a few months before the official release, so what if I instead of installing from the software centre, or using apt-get I decided to compile from the source, but the version that I decide to compile it is the same version available in the software centre, for example let's talk about VLC. The latest version available in the 12.04 is 2.08 Two flower. Is it okay if I compile it from the source in other words build it (the same version), and I'm not talking only about VLC I'm talking about any other package, is it okay?
One last word: I know that some of you may ask why compile it when it's available after doing a few clicks, but I'm just asking is it okay?
Thank you for reading

---

### Post by oldos2er on 2015-05-25
It should be ok, though I don't know why you might want to compile and install the same version you already have.

---

### Post by Vladlenin5000 on 2015-05-25
> **oldos2er said:**
> It should be ok, though I don't know why you might want to compile and install the same version you already have.
+1

We usually do that but only for versions not yet packaged and other software not available at the repos, mostly our own apps.

---

### Post by cariboo on 2015-05-25
This topic really doesn't belong in the New to Ubuntu section, by the time a user is confident enough to start compiling packages from source, the are no longer newbies. Moved to General Help.

---

### Post by monkeybrain20122 on 2015-05-25
There are reasons to compile even if the same version is in the repo. For example, to enable options that are not enabled in the standard packages, or do other customizations. I compile vlc from source because I like to use ffmpeg instead of libav, and for a while it seems that the vdpau option is not enabled in the Ubuntu build (at least for 13.10 and 14.04) while it has been available upstream for quite a while.  There are a few others like that.

---

### Post by SeijiSensei on 2015-05-25
Most packages conform to some basic standards.  In particular, most applications compile with the command sequence:
```

cd ~
mkdir -p build
cd build
tar xzvf /path/to/the/source/tarball.tgz
cd source_directory
./configure
make
sudo make install

```
"make install" will place all the files in the /usr/local tree.  The standard user profile creates a path that looks in /usr/local before it looks in /usr where packaged software resides.
```
$ echo $PATH
/home/seiji/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

Daemons are more complicated because they are started by init using configuration files in /etc/init.  You can "trick" the scripts to use a new executable in, say, /usr/local/sbin by using symbolic links like this:
```

cd /usr/sbin
sudo mv some_daemon some_daemon.dist
sudo ln -s /usr/local/sbin/some_daemon

```
Now when the script launches the daemon it expects to find in /usr/sbin it will run the version in /usr/local/sbin instead.  Using a symbolic link lets you revert to the original program if something goes wrong.

---

### Post by monkeybrain20122 on 2015-05-25
It is good to have checkinstall if you compile from source. make install tends to scatter files all over the file system but checkinstall creates a .deb that will show up in the package manager so it is easy to remove if needs to. If you are compiling the same version makes sure you report the version of the self build to be higher than that of the repo's version when running checkinstall (e.g if vlc version in repo is 2.08.2 then you should make your self build 2.08.3 so it won't get "upgraded" by the package manager)

checkinstall is in the repo. To use it, run s'sudo checkinstall" instead of "sudo make install" in the last step of compiling and follow the prompt.

---

