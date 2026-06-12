---
title: "Banshee 0.11 HOWTO"
date: 2006-09-20
forum: General Help
---

### Post by GameGod on 2006-09-20
**Updated Sept 26, 2006**: Added iPod support stuff...

Hi guys,

I've posted a [HOWTO for installing Banshee 0.11]("http://linuxrevolution.blogspot.com/2006/09/howto-banshee-011-ubuntu.html") from source on my blog. I've also written [a little blurb on the 0.11 release including some screenshots]("http://linuxrevolution.blogspot.com/2006/09/banshee-011-released.html"), if you're interested.

I'll save you the trouble and paste the article here for you too:


**IMPORTANT NOTE:**
If you have the QuinnStorm repositories enabled (for Compiz/XGL stuff), you might encounter this compile error: "/bin/grep: can't read /usr/lib/libXrender.la: No such file or directory" or something along those lines. The necessary fix can be found here. (I just ended up removing the "/usr/lib/libXrender.la" part of that line and it fixed it, and I think that's probably a safer route.)
Ubuntu 6.10/Edgy Eft Users: Updated Banshee packages will probably hit the Edgy repositories, so just hold tight for a bit and hopefully an updated package will get pushed through the usual Ubuntu update notifier.

To follow this HOWTO, just punch (ie. copy and paste) the commands listed into a terminal. Good luck!

**1. Install prerequisites**

First, make sure you have the Universe repository enabled. If you're unsure, [here's instructions on how to check and enable it]("https://help.ubuntu.com/community/Repositories/Ubuntu").
```
sudo apt-get build-dep banshee
sudo apt-get install libavahi-cil
sudo apt-get build-dep libipoddevice0
sudo apt-get install libgtop2 libgtop2-dev libsgutils libsgutils-dev
wget http://banshee-project.org/files/libipoddevice/libipoddevice-0.5.0.tar.gz
wget http://banshee-project.org/files/ipod-sharp/ipod-sharp-0.6.2.tar.gz
tar -xvzf libipoddevice-0.5.0.tar.gz
tar -xvzf ipod-sharp-0.6.2.tar.gz
```

Now, in order to have **iPod support**, we're going to install libipoddevice and ipod-sharp:

```

cd libipoddevice-0.5.0
./configure --prefix=/usr
make
sudo make install
cd ..

cd ipod-sharp-0.6.2
./configure --prefix=/usr
make
sudo make install
```

**2. Download Banshee 0.11**

```
wget http://banshee-project.org/files/banshee/banshee-0.11.0.tar.gz
wget http://www.banshee-project.org/files/banshee-official-plugins/banshee-official-plugins-0.11.0.tar.gz

```
**3. Extract and configure**

```
tar -xvzf banshee-0.11.0.tar.gz
tar -xvzf banshee-official-plugins-0.11.0.tar.gz
cd banshee-0.11.0
./configure --prefix=/usr --enable-avahi --disable-docs
```

I suggest leaving avahi enabled here as I did so that DAAP sharing works. (It lets you share your music library with iTunes, Limewire, etc. users, as well as listen to other peoples'.) iPod support should be automatically detected if you followed the iPod steps above.

**4. Build and install Banshee**

```
make
sudo make install
```


**5. Configure, build, and install the plugins**

```
cd banshee-official-plugins-0.11.0
./configure --prefix=/usr
make
sudo make install
```


**6. Run Banshee!**

Either from the console run "banshee" or launch it from the "Applications->Sound & Video" menu in GNOME.

That's it! I've tested this on an "almost" fresh-install Ubuntu 6.06/Dapper Drake machine, but if this doesn't work for you, leave a comment and I can try to help you figure it out. :)

---

### Post by gamma on 2006-09-20
When running apt-get build-dep banshee I get this error msg:
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for banshee could not be satisfied.

Any ideas?

---

### Post by GameGod on 2006-09-20
Do you have the universe/multiverse repositories enabled?

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by furste on 2006-09-20
everything works fine until i get to ./configure yadayada, at which point i get this [EDIT: i should add that a great deal transpires in the ./configure process before this]:
```
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for install... /usr/bin/install -c
checking pkg-config is at least version 0.9.0... yes
checking for HELIX_REMOTE... checking for MONO... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

i'm on a relatively fresh ubuntu 6.06 machine and i've been trying to install the 'missing' packages (mono and glib) via synaptic to no avail.

Thanks in advance!


Furste

---

### Post by xplode_me on 2006-09-20
joel@supernova:~/banshee$ sudo apt-get build-dep banshee
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for banshee
joel@supernova:~/banshee$ 


I do have universe/multiverse.

Can anyone tell us what the buil-dep banshee packages are?

---

### Post by GameGod on 2006-09-20
> **xplode_me said:**
> joel@supernova:~/banshee$ sudo apt-get build-dep banshee
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for banshee
joel@supernova:~/banshee$ 


I do have universe/multiverse.

Can anyone tell us what the buil-dep banshee packages are?

I'm not sure how to find out what the build-deps are... anyone have any ideas?

Did you happen to notice if you had both the "Source" and "Binary" repositories enabled for Universe? (The wiki might be incomplete...)
The build-dep command should work if you have the "Source" repo enabled also...

---

### Post by anodizer on 2006-09-20
The tray icon and the program icon are missing, is there a fix for that?

---

### Post by niko7865 on 2006-09-20
Thanks for the guide, everything worked except the new plugins (they don't show up in the Plugins dialog). Any idea whats wrong? I did have 0.10.10 installed from apt-get but i removed it before following the guide.

Also I get this error, but it doesn't seem to stop anything from working.

```
(Banshee:16049): Gtk-CRITICAL **: gtk_tree_view_get_cell_area: assertion `GTK_WIDGET_REALIZED (tree_view)' failed

```

---

### Post by Amodef on 2006-09-21
Thanks GameGod ! That's amazing, it's really nice !

> **anodizer said:**
> The tray icon and the program icon are missing, is there a fix for that?

And I get this problem too.

---

### Post by anodizer on 2006-09-22
Ok here are some debs for Banshee, Banshee official plugins, album art, and ShowTrackonChange. I think you 'll have no problems installing them.

[http://rapidshare.de/files/34049285/Banshee.tar.gz.html](http://rapidshare.de/files/34049285/Banshee.tar.gz.html)

---

### Post by David Corrales on 2006-09-22
I might add that instead of **make install** you might want to use **checkinstall** to generate a .deb that gets managed with synaptic.

Edit: **checkinstall** does work nicely but you need to install the *monodoc* package or you'll get a problem about an xml not found during the package building.

---

### Post by Confuse on 2006-09-24
This is the error I've encountered after installing the debs. I have dbus-cil installed to the latest stable version, by the way.

damian@pompey:~$ banshee
&#65279;libdbus-glib-1
System.DllNotFoundException: libdbus-glib-1
in (wrapper managed-to-native) Banshee.BansheeEntry:dbus_g_thread_init ()
in <0x0003d> Banshee.BansheeEntry:Startup (System.String[] args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
in <0x00095> Banshee.Gui.CleanRoomStartup:Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00011> Banshee.Base.Branding:get_ApplicationIconName ()
in <0x0000e> Banshee.Base.IconThemeUtils:SetWindowIcon (Gtk.Window window)
in <0x0048a> Banshee.Gui.Dialogs.ExceptionDialog:.ctor (System.Exception e)
in <0x000db> Banshee.Gui.CleanRoomStartup:Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args)
in <0x00038> Banshee.BansheeEntry:Main (System.String[] args)

---

### Post by GameGod on 2006-09-24
Do you have "libdbus-glib-1-2" installed?

---

### Post by RafRaf on 2006-09-24
Hi, I followed the instructions on the c homepage on how to install 0.11 on Dapper:

A Dapper repository of many thing mono including banshee and dependencies are available by adding this line to /etc/apt/sources.list:
deb [http://apebox.org/badgerexplosion](http://apebox.org/badgerexplosion) ./

Banshee upgraded and is working fine but now beagle stoped working :( 
There is a thread about it. Seams like it is not compatible..
[http://www.ubuntuforums.org/showthread.php?t=209148&highlight=beagle](http://www.ubuntuforums.org/showthread.php?t=209148&highlight=beagle)

---

### Post by Craig Caldwell on 2006-09-25
I'm not sure how to get full Ipod support with this build.
My Ipod firmware is still 2006-06-28.
I can see my Ipod in Banshee.
I have the Sync ipod button.
When I click on the Sync button It will look like something is happening.
But then it will say Processing...............................
Forever.

Please help.

---

### Post by GameGod on 2006-09-26
Hi Craig, I've just updated the HOWTO with instructions on how to get iPod support working... Try following it again with the new instructions and you should be on your way.
:)

---

### Post by fluid on 2006-10-04
> **furste said:**
> everything works fine until i get to ./configure yadayada, at which point i get this [EDIT: i should add that a great deal transpires in the ./configure process before this]:
```
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for install... /usr/bin/install -c
checking pkg-config is at least version 0.9.0... yes
checking for HELIX_REMOTE... checking for MONO... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

i'm on a relatively fresh ubuntu 6.06 machine and i've been trying to install the 'missing' packages (mono and glib) via synaptic to no avail.

Thanks in advance!


Furste

maybe this helps:

sudo apt-get install libmono0 libmono-dev

helped me :cool:

---

### Post by fluid on 2006-10-05
now banshee 0.11 works, but it can't handle my library (+7000 files), due to performance problems i will stay with rhythmbox... :???:

---

### Post by PermuZero on 2006-10-06
I get the same "/usr/lib/libXrender.la" problem.  Where did you remove it from?  :-k

---

### Post by mighty_falcon on 2006-10-14
musch easier way, use the reposatory

[http://banshee-project.org/Distributions/Ubuntu](http://banshee-project.org/Distributions/Ubuntu)

---

### Post by Yap on 2006-10-15
Ok...so I tried to follow the instructions in your excellent HOWTO, but had not luck.

Tried the Apebox repository as mentioned on the Banshee Ubuntu page...also no luck.

Bit of digging about revealled that the actual repository to add is located on this page: [http://directhex.mfgames.com/]("http://directhex.mfgames.com/")

Follow the instructions re. adding the GPG key and then the repository.

I then used the Synaptic Package Manager to update (refresh) the sources and install the updated Banshee files. 

Note: if you already have version 0.10 installed the update manager will prompt to automatically update Banshee once you have added the new repository (and updated). You will still need to specify the installation of the plug-ins separately.

Hope this helps.

Yap.

---

### Post by Dangling on 2006-10-16
> **Yap said:**
> 
Bit of digging about revealled that the actual repository to add is located on this page: [http://directhex.mfgames.com/]("http://directhex.mfgames.com/")

Follow the instructions re. adding the GPG key and then the repository.

I then used the Synaptic Package Manager to update (refresh) the sources and install the updated Banshee files. 


I followed the directions on the website. But when I tried to update (using apt-get and aptitude) I get MD5Sum mismatch. Any thoughts on how to fix this?

Thanks

---

### Post by drobvice on 2006-10-18
I now have an additional 62 updates available (gstreamer!?) after adding that repos.  I'm skeerd. :|

---

### Post by sethmahoney on 2006-10-19
<s>Does anyone know how to make banshee, rather than rhythmbox, open when I plug in my iPod?</s>

Nevermind, found the answer elsewhere.

---

### Post by David Corrales on 2006-10-19
> **drobvice said:**
> I now have an additional 62 updates available (gstreamer!?) after adding that repos.  I'm skeerd. :|

He maintains a repository of the whole updated mono. I'm using with no problems so far, but if you want to "spoil" your vainilla install, just build banshee from source.

---

### Post by subiet on 2006-11-05
"checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
        gstreamer-base-0.10 >= 0.10.3
        gstreamer-plugins-base-0.10 >= 0.10.3
        gstreamer-controller-0.10 >= 0.10.3
        gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:
"


this is the error, after installing like a gizzilion dev libs in between, and i just can't find these packages, even from badgerport, any help??

---

### Post by drobvice on 2006-11-05
I ended up installing edgy and now I have the almost newest version.  It loads pretty quickly as well!

---

