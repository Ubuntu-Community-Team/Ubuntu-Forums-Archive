---
title: "netatalk, version, ssl support"
date: 2005-06-26
forum: General Help
---

### Post by manders2k on 2005-06-26
So, I want to want to use an Ubuntu Linux computer as a file and print server for two Macs running OS X.  I decided that netatalk was the best (fastest, most mac-integrated) way to go.

The first thing I tried was to compile netatalk 2.0.3 from source, as I've seen conflicting reports about pre-2.0 versions having terrible, horrendous issues with OS X.  Anyone know if there is any truth to this, and what the issues are?  I ran configure as: "./configure --enable-debian", and attempted to satisfy all the dependencies I could identify before I built it.  It built fine, but I was totally unable to connect to the afpd daemon once it was installed and running (when using the Finder to "connect to server", it was unable to authenticate, and refused to ask for a username/password).  The configuration was the default as shipped with the source (should offer a home directory). 

So, I uninstalled it ("make uninstall") and tried the more obvious "apt-get install netatalk" (even though the version is 1.6.4a, alleged source of problems for OS X).  It installed and I was able to connect to it in its default configuration, but could only authenticate with cleartext passwords.  A little further investigation shows that uams_dhx.so (the module which allows encrypted password usage) does not ship with the package.  The README.Debian file that was included with the package tells me that the Debian project refuses to link programs to OpenSSL due to a possible license conflict, and hence uams_dhx.so is not included.  But, I'm welcome to rebuild the package with the DEB_BUILD_OPTIONS environment variable set to "ssl", and everything should be hunky dory.  Thank you Debian for making things easy and convenient.

I tried teaching myself to rebuild a Debian package, but have been so far unable to build this package successfully.  Currently, it is complaining about being unable to link to cracklib during the build process (though I did install cracklib2 and cracklib-runtime through synaptic or apt-get, I forget which; I also edited /etc/ld.so.conf to include /lib/ and /usr/lib/ and ran ldconfig to try to get it to link properly which didn't work; I didn't investigate what configure was doing to perform the test and re-teach myself all the crazy rules which is the linking process on Linux).

Extreme frustration is starting to set in.

Could someone please explain to me what the proper or best way to get a functioning copy of netatalk running (that does include uams_dhx.so and/or the pam equivalent) on a more or less fresh install of Ubuntu 5.04?

If someone is reading this who has some control of the Ubuntu documentation, I would suggest documenting the limitations of the netatalk package as distributed, and how to get around them.

Also, does anyone know why there isn't a netatalk package from the 2.0 line available?

Thanks for any help.

---

### Post by AlexMorin on 2006-03-09
Same issue with a **5.10 Edubuntu install**. uams_dhx.so is not included in the **Netatalk 2.0.31ubuntu1** that aptitude installled through the "universe" servers.
Why is this package still in universe, and not the main section? It's no big deal changing up the sources.list, but still, I'd like for Netatalk to be supported by Ubuntu/Edubuntu.
Should I mention that the education market has quite a lot of installed Macs?

So, if anyone has a way to get encrypted passwords working on Edubuntu for Mac clients, I'd be most thankful!

BTW, a really nice setup guide is online at the package's site : [http://netatalk.sourceforge.net/2.0/htmldocs/](http://netatalk.sourceforge.net/2.0/htmldocs/)

---

### Post by AlexMorin on 2006-03-20
Anyone?

Sorry for the bump, but this is a huge problem for me! I can't put this server in production using clear-text passwords.

And samba has it's bugs with Mac files.

---

### Post by gruepig on 2006-04-02
OS X doesn't natively support appletalk.  For better OS X support, try samba or nfs.

---

### Post by AlexMorin on 2006-04-03
Right, but I need OS 9 support. So Netatalk it is...

---

### Post by gruepig on 2006-04-04
You want cracklib2-dev for the headers.  (I'm not sure why apt doesn't just pull it in.)

I just installed netatalk with the following:

apt-get source netatalk
sudo apt-get build-dep netatalk
sudo apt-get install cracklib2-dev
cd netatalk-2.0.3
DEB_BUILD_OPTIONS=ssl debuild
sudo dpkg -i ../netatalk-*.deb

I think the passwords are being sent encrypted.  tcpflow indicates that the password was being sent "AFP3.1.DHCAST128".  It looks like directory contents (ls) is sent clear text, but file contents is sent encrypted.

---

### Post by AlexMorin on 2006-04-13
Solved!

Thanks gruepig!

Refer to this thread for complete instructions and proper syntax. Enjoy!

[http://ubuntuforums.org/showpost.php?p=918060&postcount=16](http://ubuntuforums.org/showpost.php?p=918060&postcount=16)

---

### Post by n8gray on 2006-07-14
I followed this procedure and the uams_dhx.so module is still not built!  This is really annoying...

](*,)

**UPDATE**
It turns out you need to install libssl-dev as well.  Add
```
sudo apt-get install libssl-dev
```
to your procedure, before you build the package, and all will be well.

---

### Post by AlexMorin on 2006-07-14
Could you provide somme more info? Where does this break for you? Any error messages during the procedure? 
Did you follow the revised instructions : [http://ubuntuforums.org/showpost.php?p=918060&postcount=16](http://ubuntuforums.org/showpost.php?p=918060&postcount=16) ?

---

