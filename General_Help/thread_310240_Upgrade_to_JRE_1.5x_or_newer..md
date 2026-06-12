---
title: "Upgrade to JRE 1.5x or newer."
date: 2006-11-30
forum: General Help
---

### Post by sp0nge on 2006-11-30
I've been trying to install Frostwire for a day now and can NOT get jre-1_5_0_09-linux-i586-rpm.bin to install. This is the thick of it...


```
chmod a+x jre-1_5_0-linux-i586-rpm.bin
```
```
./ jre-1_5_0_09-linux-i586-rpm.bin
```

and accepted the agreement which created jre-1_5_0-linux-i586.rpm

```
rpm -iv jre-1_5_0-linux-i586.rpm
```

at which point a sub directory "jre1.5.0" should be created and JRE should be installed, but I get this:

```
error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_09-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_09-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_09-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_09-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_09-fcs.i586
        /bin/sh is needed by jre-1.5.0_09-fcs.i586

```

What is the best way to accomplish this?

---

### Post by taurus on 2006-11-30
How about

```
sudo aptitude install alien
alien jre-1_5_0-linux-i586.rpm
sudo dpkg -i jre-1_5_0-linux-i586.deb
```

---

### Post by hod139 on 2006-11-30
Or, how about 
```

sudo aptitude install sun-java5-jre
sudo update-java-alternatives -s java-1.5.0-sun

```

---

### Post by sp0nge on 2006-11-30
I installed alien and tried the code:

```
alien alien jre-1_5_0_09-linux-i586.rpm

```

which returned:

```
Cannot write to current directory. Try moving to /tmp and re-running alien.
```

which I did... 

```
carlo@Laptop:/usr/java$ cp jre-1_5_0_09-linux-i586.rpm /tmp

```

which returned: 

```
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
jre_1.5.0_09-1_i386.deb generated
```

What am I missing?

---

### Post by sp0nge on 2006-11-30
Just for fun, since I Smell my first format since I Migrated to linux, I decided to try the other route: 

```
aptitude install sun-java5-jre
```

Upon seeing "Done", I figure this was successful. 

```
update-java-alternatives -s java-1.5.0-sun
```

which returned:

```
update-java-alternatives -s java-1.5.0-sun
```

Still no luck after a restart.

---

### Post by hod139 on 2006-11-30
What happens if you type the command:
```

java -version

```

BTW, you don't have to restart after installing applications in Linux!!!

---

### Post by xopher on 2006-11-30
> **hod139 said:**
> 
BTW, you don't have to restart after installing applications in Linux!!!

Man I've told that to over 10 different people over IRC today :)

---

### Post by sp0nge on 2006-12-03
Upon your suggestion I tried 

```
java -version
```

which returned

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

Still showing the old verison.

I know there is not need to restart but I wanted to turn it off to let it sit for a while. Thanks for helping to educate me- I'm failrly new.

---

### Post by taurus on 2006-12-03
```
update-alternatives --config java
```

---

### Post by sp0nge on 2006-12-03
```
update-alternatives --config java
```

Which returns

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:
```

I have jre-1_5_0_09-linux-i586.rpm in my home folder,which is what I need to install, but what next?

---

### Post by taurus on 2006-12-03
```
alien jre-1_5_0_09-linux-i586.rpm
sudo dpkg -i jre-1_5_0_09-linux-i586.deb
sudo update-alternatives --config java
```

---

### Post by sp0nge on 2006-12-05
```
Warning: Skipping conversion of scripts in package jre: postinst postrm prermWarning: Use the --scripts parameter to include the scripts.

```

```
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
```

---

### Post by yopnono on 2006-12-06
I always run this to convert RPM to DEB (-c includes scripts)
```
fakeroot alien -c file.rpm
```
then to install
```
sudo dpkg -i file.deb
```

---

### Post by sp0nge on 2006-12-06
Ok, so I got the .rpm converted to .deb and ran

```
sudo dpkg -i jre_1.5.0_09-1_i386.deb

```

Which returned

```
Selecting previously deselected package jre.
(Reading database ...
142064 files and directories currently installed.)
Unpacking jre (from jre_1.5.0_09-1_i386.deb) ...
Setting up jre (1.5.0_09-1) ...

```

I thought this worked so I tried 

```
java -version
```

which returned 

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

Does 1.4.2-02 need to be uninstalled before 1.5_09-1 can be installed? This doen't make much sense to me but can it be so? Any other input here?

---

### Post by yopnono on 2006-12-06
Are you installing java because you need it in firefox or in some application.

If FX open the browser and type in the adress bar about:plugins and see if it's detected.

if it's not detected then you may need to create a link from the java plugin to fx plugin folder

for OOo tool/option/java.

---

### Post by taurus on 2006-12-06
You need to run this command to tell the system to use the newer version of java...  Make sure you use the arrow key to move to the latest version and place a * in front of it with the Tab key (or space key).

```
sudo update-alternatives --config java
java -version
```

---

### Post by sp0nge on 2006-12-06
I am installing java for both using Frostwire AND I have a website I need to access for work that requires it (but does not work with the current version). The browser recognizes the older version.

Upon the suggestion to 

```
 update-alternatives --config java

```

which returned

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java

```

At the risk of looking slower than the blonde I am, none of these are the version I'm trying to locate?

---

### Post by taurus on 2006-12-06
What's the output of this command from a terminal?

```
locate java
```

---

### Post by sp0nge on 2006-12-06
The list is too long to post (pages upon pages) here is the last page worth

```
/usr/share/omf/java-policy
/usr/share/omf/java-policy/java-policy-C.omf
/usr/share/vim/vim64/compiler/javac.vim
/usr/share/vim/vim64/ftplugin/java.vim
/usr/share/vim/vim64/indent/java.vim
/usr/share/vim/vim64/syntax/java.vim
/usr/share/vim/vim64/syntax/javacc.vim
/usr/share/vim/vim64/syntax/javascript.vim
/usr/share/glib-java
/usr/share/glib-java/macros
/usr/share/glib-java/macros/am_path_docbook.m4
/usr/share/glib-java/macros/jg_common.m4
/usr/share/glib-java/macros/am_path_gcj.m4
/usr/share/glib-java/macros/jg_lib.m4
/usr/share/glib-java/macros/jg_check_nativecompile.m4
/usr/share/glib-java/macros/ac_prog_javac_works.m4
/usr/share/glib-java/macros/ac_prog_javadoc.m4
/usr/share/glib-java/macros/ac_prog_javac.m4
/usr/share/glib-java/macros/ac_prog_jar.m4
/usr/share/libgtk-java
/usr/share/libgtk-java/macros
/usr/share/libgtk-java/macros/jg_gnome_java.m4
/usr/share/libgtk-java/macros/jg_gtk_java.m4
/usr/share/services/kjavaappletviewer.desktop
/usr/java
/usr/java/jre-1_5_0_09-linux-i586-rpm.bin
/usr/java/jre-1_5_0_09-linux-i586.rpm

```

---

### Post by yopnono on 2006-12-06
/usr/java
/usr/java/jre-1_5_0_09-linux-i586-rpm.bin
/usr/java/jre-1_5_0_09-linux-i586.rpm

remove them. Did you download the RPM or BIN?

---

### Post by yopnono on 2006-12-06
Anyhow. I think you should start all over.
[http://java.com/en/download/help/5000010500.xml](http://java.com/en/download/help/5000010500.xml)

And if you like to try the new beta.
[http://java.sun.com/javase/downloads/ea.jsp](http://java.sun.com/javase/downloads/ea.jsp)

---

### Post by sp0nge on 2006-12-06
I downloaded the .bin which I think got converted to a .rpm and then to .deb somewhere along this frusterating path...

I'll remove them, no prob, but are we sure I don't need these anymore?

---

### Post by taurus on 2006-12-06
> **sp0nge said:**
> The list is too long to post (pages upon pages) here is the last page worth

```
/usr/share/omf/java-policy
/usr/share/omf/java-policy/java-policy-C.omf
/usr/share/vim/vim64/compiler/javac.vim
/usr/share/vim/vim64/ftplugin/java.vim
/usr/share/vim/vim64/indent/java.vim
/usr/share/vim/vim64/syntax/java.vim
/usr/share/vim/vim64/syntax/javacc.vim
/usr/share/vim/vim64/syntax/javascript.vim
/usr/share/glib-java
/usr/share/glib-java/macros
/usr/share/glib-java/macros/am_path_docbook.m4
/usr/share/glib-java/macros/jg_common.m4
/usr/share/glib-java/macros/am_path_gcj.m4
/usr/share/glib-java/macros/jg_lib.m4
/usr/share/glib-java/macros/jg_check_nativecompile.m4
/usr/share/glib-java/macros/ac_prog_javac_works.m4
/usr/share/glib-java/macros/ac_prog_javadoc.m4
/usr/share/glib-java/macros/ac_prog_javac.m4
/usr/share/glib-java/macros/ac_prog_jar.m4
/usr/share/libgtk-java
/usr/share/libgtk-java/macros
/usr/share/libgtk-java/macros/jg_gnome_java.m4
/usr/share/libgtk-java/macros/jg_gtk_java.m4
/usr/share/services/kjavaappletviewer.desktop
/usr/java
/usr/java/jre-1_5_0_09-linux-i586-rpm.bin
/usr/java/jre-1_5_0_09-linux-i586.rpm

```

```
sudo alien /usr/java/jre-1_5_0_09-linux-i586.rpm
sudo dpkg -i /usr/java/jre-1_5_0_09-linux-i586.deb
sudo update-alternatives --config java
java -version
```

---

### Post by sp0nge on 2006-12-06
```
sudo dpkg -i /usr/java/jre-1_5_0_09-linux-i586.deb
dpkg: error processing /usr/java/jre-1_5_0_09-linux-i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/java/jre-1_5_0_09-linux-i586.deb

```


It's starting to feel like I'm doing something wrong here...](*,)

---

### Post by taurus on 2006-12-06
Did you remember to convert the .rpm to .deb first?

```
sudo alien /usr/java/jre-1_5_0_09-linux-i586.rpm
```

---

### Post by Perfect Storm on 2006-12-06
Uninstall the 1.5 java you have then check this [http://ubuntuforums.org/showthread.php?t=311031&highlight=java](http://ubuntuforums.org/showthread.php?t=311031&highlight=java)

---

### Post by sp0nge on 2006-12-06
```
sudo alien jre_1.5.0_09-1_i386.deb
carlo@Laptop:~$ sudo dpkg -i jre-1_5_0_09-linux-i586.deb
dpkg: error processing jre-1_5_0_09-linux-i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 jre-1_5_0_09-linux-i586.deb

```

---

### Post by Perfect Storm on 2006-12-06
*nevermind*

---

### Post by sp0nge on 2006-12-06
Totally off topic, but AI, I love that avatar! Polar bears are my fav! Did you happen to create that? I'm trying to get into graphics myself. That is if I don't throw this laptop against a wall!

---

### Post by Perfect Storm on 2006-12-06
I found the Polarbear picture (Can't remember where, been awhile), then I added the Ubuntu logo to it with gimp and because it's soon xmas I added some xmas stuff :D

---

### Post by sp0nge on 2006-12-06
I tried again... 

```
sudo dpkg -i jre_1.5.0_09-1_i386.deb
Selecting previously deselected package jre.
(Reading database ... 142064 files and directories currently installed.)
Unpacking jre (from jre_1.5.0_09-1_i386.deb) ...
Setting up jre (1.5.0_09-1) ...
carlo@Laptop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:

```

Still shows the old version. What am I missing?!

---

### Post by Perfect Storm on 2006-12-06
Why don't you try the link I provided? It shows you how to build a .deb package of jre1.5 update 10

---

### Post by sp0nge on 2006-12-06
sorry.. I missed the link the first time. I tried it and returned...

```
sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
Package java-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package java-package has no installation candidate

```

---

### Post by Perfect Storm on 2006-12-06
```
cat /etc/apt/sources.list
```

Seems like you havn't enable multiverse.

---

### Post by sp0nge on 2006-12-06
```
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://wine.budgetdedicated.com/apt dapper main
deb http://wine.budgetdedicated.com/apt dapper main
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

```

---

### Post by Perfect Storm on 2006-12-06
```
sudo nano /etc/apt/sources.list
```

add:

[b]######### Multiverse #######

## Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
[/b]

also uncomment the lines that have one # infront.

save and exit, then;

```
sudo apt-get update
```

---

### Post by sp0nge on 2006-12-06
I ran back through synaptic and enabled the multiverse repos.. the same data returned.

---

### Post by Perfect Storm on 2006-12-06
No they are some restricted parts of multiverse (backports).

---

### Post by sp0nge on 2006-12-06
well I think we're getting closer- you're on to something...

```
It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:25 http://packages.freecontrib.org dapper Release.gpg [189B]
Hit http://packages.freecontrib.org dapper Release
Err http://packages.freecontrib.org dapper Release

Get:26 http://packages.freecontrib.org dapper Release [9452B]
Ign http://packages.freecontrib.org dapper Release
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Fetched 363kB in 4s (73.6kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages - open (2 No such file or directory)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by yopnono on 2006-12-06
> **sp0nge said:**
> well I think we're getting closer- you're on to something...


I think you are going to have a lot of beans when this is done :)

---

### Post by sp0nge on 2006-12-06
This is the first time I've run into something I cant solve (either on my own or with limited help and lots of reading)... 

Now I actually have something I cant get through and I hope it will come in handy for someone else along the way... the more beans the thicker the ubuntu!?!

---

### Post by Perfect Storm on 2006-12-06
> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

It's a security lock, just do this;
```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
sudo apt-get update
```

> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
Not a serious error, it just means there's duplicate of the universe in the source list, just leave it.

If you want to make a clean and full sourcelist check here: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by sp0nge on 2006-12-06
Two steps forward.. one step back:

```
 fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin
Error: The file "jre-1_5_0_09-linux-i586.bin" does not exist.

```

---

### Post by Perfect Storm on 2006-12-06
Change 09 to 10 a newer version is out. (jre-1_5_0_09-linux-i586.bin to jre-1_5_0_10-linux-i586.bin)

Also make sure before installing the new java package to uninstall the converted .deb first.

---

### Post by sp0nge on 2006-12-06
```
 fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin
Error: The file "jre-1_5_0_10-linux-i586.bin" does not exist.

```

Do I need an updated .rpm file as well?

---

### Post by sp0nge on 2006-12-06
sorry. I'm getting ahead of myself- frusteration has take over...

---

### Post by Perfect Storm on 2006-12-06
Where to did you downloaded the .bin file too? You need to cd /to/the/right/place

> Do I need an updated .rpm file as well?
nope, just download the .bin file

---

### Post by sp0nge on 2006-12-06
```
 sudo dpkg -r jre_1.5.0_09-1_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

Apparently I don't yet understand the process to do this?!

---

### Post by Perfect Storm on 2006-12-06
Change  sudo dpkg -r jre_1.5.0_09-1_i386.deb to  sudo dpkg -r jre_1.5.0_10-1_i386.deb

It's because th howto was written when java was on update 9 and the latest is is update 10, so you have to change it a little bit.

---

### Post by sp0nge on 2006-12-06
```
carlo@Laptop:~$ sudo dpkg -r jre_1.5.0_10-1_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by Perfect Storm on 2006-12-06
okay, question. Are you trying to install the package from thte howto or removing the old package?

---

### Post by sp0nge on 2006-12-06
apparently I can't delete the old one... I'm off to download the new version and see what happens.

---

### Post by sp0nge on 2006-12-06
I'm trying to remove the old one first ... then on to install the new.

---

### Post by Perfect Storm on 2006-12-06
Well removing the previous one;
```
sudo aptitude remove sun-j2re1.5
```

or open synaptic and search for sun-j2re.

---

### Post by sp0nge on 2006-12-06
You're my new best friend! Now that I have removed the old, Do I need to go to the website and download this v10 or resume from the link you posted?

```
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb
sudo update-alternatives --config java

```

---

### Post by Perfect Storm on 2006-12-06
Well as long you get the jre 1.5 update 10 .bin file ;)

---

### Post by sp0nge on 2006-12-06
downloading jre-1_5_0_10-linux-i586.bin

---

### Post by sp0nge on 2006-12-06
```
Reading package lists... Done
~/Desktop$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
~/Desktop$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:

```

Am I wrong here, or are we still missing something?

---

### Post by Perfect Storm on 2006-12-06
Try:
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by sp0nge on 2006-12-06
...which returned:

```
sudo update-java-alternatives -s java-1.5.0-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun

```

---

### Post by Perfect Storm on 2006-12-06
You're running 32-bit Ubuntu?

---

### Post by sp0nge on 2006-12-06
Nope. plain 'ol dapper ..

---

### Post by sp0nge on 2006-12-06
Sorry.. that should be yes- tis not a 64 bit.

---

### Post by sp0nge on 2006-12-06
At least I'm not feeling like a total dummy!

I've toiled over this for days now to no avail. I know the machine is capable, I ran java on it when I Was window$ dependant.

*prays to the ubuntu gods*

---

### Post by Perfect Storm on 2006-12-07
Sorry needed some sleep. While doing the howto step did any complain/error showed up?

Try this - 
```
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```

Now go to firefox and type **about :plugins** (without the space between **about** and **:plugins**) in the adresse bar.
What does it say under java?

Also give me the out put of:
```
locate sun-j2re1.5
```

---

### Post by yopnono on 2006-12-07
Honestly, do you really need to convert it to a deb. If so why?
Why don't you just install it like normal.

[http://java.com/en/download/help/5000010500.xml](http://java.com/en/download/help/5000010500.xml)

---

### Post by Olav on 2006-12-07
Take a look at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox) - that will sort you out.

---

### Post by sp0nge on 2006-12-07
Thank god- I'd though you'd given up on me, AI!

```
 sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```

which returns:
```
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so' to `/usr/lib/j2re1.5-sun/plugin/i386/ns7-gcc29/libjavaplugin_oji.so': File exists

Next I tried:

[CODE]locate sun-j2re1.5
```

Which returned

```
/home/carlo/Desktop/sun-j2re1.5_1.5.0+update10_i386.deb
/usr/share/java-package/sun-j2re1.5
/usr/share/java-package/sun-j2re1.5/install
/usr/share/java-package/sun-j2re1.5/remove

```

---

### Post by sp0nge on 2006-12-07
As for the plugins, this is the list under Java (still showing 1.4)

Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes

---

### Post by Perfect Storm on 2006-12-07
Hmmm...try uninstall blackdown java 1.4 and then reinstall sun java 1.5
after that run the java reconfigure command.

---

### Post by sp0nge on 2006-12-07
So I removed 1.4 (I think)

```
sudo aptitude remove sun-j2re1.4
```

At the end, it said "Done" so I continued...

```
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
```

Again, these seemed to work, so I press onward...

```
fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin
```

Which went on to unpack and created sun-j2re1.5_1.5.0+update10_i386.deb on the desktop... and on and on we go...

```
sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb

```

which returns more apparent success...

```
Selecting previously deselected package sun-j2re1.5.
(Reading database ... 166648 files and directories currently installed.)
Unpacking sun-j2re1.5 (from sun-j2re1.5_1.5.0+update10_i386.deb) ...
Setting up sun-j2re1.5 (1.5.0+update10) ...

```

since this seemed to work, I ran the update...

```
sudo update-alternatives --config java
```

And this time I See it!!!

```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java
      4        /usr/lib/j2re1.5-sun/bin/java


```

So I selected #4 and get 

```
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

```

And just to check... 

```
java -version
```

which returns:

```
java version "1.5.0_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Client VM (build 1.5.0_10-b03, mixed mode, sharing)

```

By Jove I think you got it!

I check the plugins for firefox- just to be sure:

Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes

STILL seeing v1.4, I decide to try Frostwire too... which works oddly enough..

---

### Post by taurus on 2006-12-07
You now need to copy/move the "libjavaplugin_oji.so" from /usr/lib/j2re1.5-sun/plugins to /usr/lib/mozilla-firefox/plugins!

---

### Post by sp0nge on 2006-12-07
from /usr/lib/j2re1.5-sun/plugin, I tried to copy the file:

```
cp libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugin
```

but there is file here... 

```
cp: cannot stat `libjavaplugin_oji.so': No such file or directory

```

---

### Post by sp0nge on 2006-12-07
Ok, so I finally found the file libjavaplugin_oji.so and copied it to folder
/usr/lib/mozilla-firefox/plugin

```
 sudo cp libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugin

```

It seemed to work, taking me back to the input prompt, so I checked the plugins in firefox again- STILL Seeing v1.4

---

### Post by sp0nge on 2006-12-07
ok .. I looked a bit deeper and realized I was copying to "plugin" and not "plugins", so I changed that and finally see the file in the correct path- I think I'm on the right track.... so I restart and check the plugins again- still seeing v1.4

Looking back in the terminal, I see:

```
 ls
libflashplayer.so     libswfdecmozilla.so   libunixprintplugin.so
libjavaplugin_oji.so  libtotem_mozilla.so
libjavaplugin.so      libtotem_mozilla.xpt

```

Thinking libjavaplugin_oji.so is conflicting with libjavaplugin.so , and not finding much other help, I remove libjavaplugin.so 

```
sudo rm libjavaplugin.so

```

Now, I'm thinking that was a mistake- I check the plugins and see NO java recognized at all!!

---

### Post by taurus on 2006-12-07
You need to restart firefox when you copy new java plugins...

---

### Post by sp0nge on 2006-12-07
I have .. time and time again. Now, there is NO java recognized!

I see the flash plugins, and the totem plugins, but NOTHING for java now.

---

### Post by taurus on 2006-12-07
I guess because you removed it.  Paste the output of this command from a terminal here then!

```
sudo find  /  -name  libjavaplugin.so  -print
```

---

### Post by sp0nge on 2006-12-07
```
find: WARNING: Hard link count is wrong for /proc/8039: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
/usr/lib/netscape/plugins-libc6/libjavaplugin.so
/usr/lib/j2se/1.4/jre/plugin/i386/netscape4/libjavaplugin.so
/usr/lib/mozilla/plugins/libjavaplugin.so

```

---

### Post by taurus on 2006-12-07
Did you happen to remove the java plugin for your new version, 1.5, since it's not on the list of that output???

---

### Post by sp0nge on 2006-12-07
If I did, I didn't do it on purpose! Artificial Intelligence told me to copy libjavaplugin_oji.so into /usr/lib/mozilla-firefox/plugins after the install, which I did... but Firefox was still only seeing v1.4 when I looked at the contents, I saw both libjavaplugin_oji.so and libjavaplugin.so, which I thought might be conflicting so I removed the latter:

```
sudo rm libjavaplugin.so
```

AI Wasn't responding, so I went into IRC and was advised to re-install v1.5 which I have, but still no luck!  :confused:

---

### Post by taurus on 2006-12-07
Not sure exactly where you reinstalled java 1.5 again because the find command couldn't find the new plugin, only from version 1.4!  Do you know where you installed java 1.5?

---

### Post by sp0nge on 2006-12-07
Sorry for the confusion- I didn't mean to start the other post, but I am so frusterated with this that I was hoping for more input (you'll see quite some time with out a reply on this thread).

As for WHERE I installed, I'm not certain. I downloaded jre-1_5_0_10-linux-i586.bin to the desktop and then did the following:

```
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb
sudo update-alternatives --config java
```

---

### Post by taurus on 2006-12-07
And "java -version" reports back that you are running version 1.5?  What's the output of this command from a terminal then?

```
sudo / -name java -print
```

---

### Post by sp0nge on 2006-12-07
Yes, the version shows 1.5

the other returned:

```
sudo: /: command not found

```

---

### Post by hod139 on 2006-12-07
I know it is late in the thread and probably too late, but why not install the repository version of Sun's java like I had mentioned earlier.  It seems like a lot of these linking issues would not exist.  After the multiverse was enabled, it should have been as simple as removing the 1.4 version, then using apt and update-java-alternatives to install the 1.5.

---

### Post by taurus on 2006-12-07
> **sp0nge said:**
> Yes, the version shows 1.5

the other returned:

```
sudo: /: command not found

```
Sorry, it's 

```
sudo find / -name java -print
```

---

### Post by sp0nge on 2006-12-07
```

/var/lib/dpkg/alternatives/java
/etc/alternatives/java
/etc/java
/home/carlo/jre-1.5.0_09/usr/java
/home/carlo/jre-1.5.0_09/usr/java/jre1.5.0_09/bin/java
/home/carlo/jre-1.5.0_09/debian/jre/usr/java
/home/carlo/jre-1.5.0_09/debian/jre/usr/java/jre1.5.0_09/bin/java
/home/carlo/jre-1.5.0_09/debian/jre/usr/java
/home/carlo/jre-1.5.0_09/debian/jre/usr/java/jre1.5.0_09/bin/java
find: WARNING: Hard link count is wrong for /proc/8039: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
/usr/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/java
/usr/lib/openoffice/share/Scripts/java
/usr/lib/java
/usr/lib/j2se/1.4/bin/java
/usr/lib/j2se/1.4/jre/bin/java
/usr/lib/j2re1.5-sun/bin/java
/usr/share/java
/usr/java
/usr/java/jre1.5.0_09/bin/java

```

---

### Post by taurus on 2006-12-07
Oh dear, how many copies of java do you have on your machine anyway???  Which version does "sudo update-alternatives --config java" point to?

---

### Post by sp0nge on 2006-12-07
All of them apparently!!! It returns:

```
There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
 +    3        /usr/lib/j2se/1.4/bin/java
*     4        /usr/lib/j2re1.5-sun/bin/java
      5        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

---

### Post by taurus on 2006-12-07
But you are using the one in "/usr/lib/j2re1.5-sun/bin/java"!

Now, what is the output of this command then?

```
ls -la /usr/lib/j2re1.5-sun/jre/plugin/i386/ns7
```

---

### Post by sp0nge on 2006-12-07
```
ls: /usr/lib/j2re1.5-sun/jre/plugin/i386/ns7: No such file or directory

```

---

### Post by taurus on 2006-12-07
How about

```
ls -la /usr/lib/j2re1.5-sun
```

---

### Post by sp0nge on 2006-12-07
```
total 176
drwxr-xr-x   8 root root  4096 2006-12-07 19:07 .
drwxr-xr-x 161 root root 36864 2006-12-07 21:23 ..
drwxr-xr-x   2 root root  4096 2006-12-07 19:07 bin
-rw-r--r--   1 root root   969 2006-11-09 18:59 CHANGES
-rw-r--r--   1 root root  2487 2006-11-09 18:59 COPYRIGHT
drwxr-xr-x   2 root root  4096 2006-12-07 19:07 debian
drwxr-xr-x   2 root root  4096 2006-12-07 19:07 javaws
drwxr-xr-x  16 root root  4096 2006-12-07 19:07 lib
-rw-r--r--   1 root root 12285 2006-11-09 18:59 LICENSE
drwxr-xr-x   4 root root  4096 2006-12-07 19:07 man
drwxr-xr-x   4 root root  4096 2006-12-07 19:07 plugin
-rw-r--r--   1 root root 13936 2006-11-09 18:59 README
-rw-r--r--   1 root root 66673 2006-11-09 18:59 THIRDPARTYLICENSEREADME.txt
-rw-r--r--   1 root root   969 2006-11-09 18:59 Welcome.html

```

---

### Post by taurus on 2006-12-07
Then,

```
cd /usr/lib/j2re1.5-sun/plugin
ls -la
```

---

### Post by sp0nge on 2006-12-07
```
total 16
drwxr-xr-x 4 root root 4096 2006-12-07 19:07 .
drwxr-xr-x 8 root root 4096 2006-12-07 19:07 ..
drwxr-xr-x 2 root root 4096 2006-12-07 19:07 desktop
drwxr-xr-x 4 root root 4096 2006-12-07 19:07 i386

```

---

### Post by taurus on 2006-12-07
```
cd i386
ls -la
```
I believe there should be a directory called ns7 so change to that too if there is one...

```
cd ns7
ls -la
```

---

### Post by sp0nge on 2006-12-07
```
/usr/lib/j2re1.5-sun/plugin/i386$ ls -la
total 16
drwxr-xr-x 4 root root 4096 2006-12-07 19:07 .
drwxr-xr-x 4 root root 4096 2006-12-07 19:07 ..
drwxr-xr-x 2 root root 4096 2006-12-07 19:07 ns7
drwxr-xr-x 2 root root 4096 2006-12-07 19:07 ns7-gcc29
/usr/lib/j2re1.5-sun/plugin/i386$ cd ns7
/usr/lib/j2re1.5-sun/plugin/i386/ns7$ ls -la
total 116
drwxr-xr-x 2 root root   4096 2006-12-07 19:07 .
drwxr-xr-x 4 root root   4096 2006-12-07 19:07 ..
-rw-r--r-- 1 root root 103432 2006-11-09 19:07 libjavaplugin_oji.so

```

---

### Post by taurus on 2006-12-07
Now, try to copy that plugin to /usr/lib/firefox/plugins...

```
sudo  cp  libjavaplugin_oji.so  /usr/lib/firefox/plugins
```
Fire up firefox and see if you have java 1.5 plugin this time!

```
about:plugins
```

---

### Post by sp0nge on 2006-12-07
```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d78

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
video/divx 	AVI video 	divx 	Yes
audio/wav 	WAV audio 	wav 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

Still no luck after re-starting firefox

---

### Post by taurus on 2006-12-07
Okay.  Shut down firefox and copy that plugins into your own $HOME directory.

```
cp  libjavaplugin_oji.so  ~/.mozilla/plugins
```
Now, fire up firefox again and see if there is a java plugin...

---

### Post by sp0nge on 2006-12-07
```
 cp  libjavaplugin_oji.so  ~/.mozilla/plugins
cp: cannot stat `libjavaplugin_oji.so': No such file or directory

```

---

### Post by taurus on 2006-12-07
You need to be in /usr/lib/j2re1.5-sun/plugin/i386/ns7 first before you run that command!!!

```
cd  /usr/lib/j2re1.5-sun/plugin/i386/ns7
cp  libjavaplugin_oji.so  ~/.mozilla/plugins
```

---

### Post by sp0nge on 2006-12-07
oops.. I thought I was.. 

```
:/usr/lib/j2re1.5-sun/plugin/i386/ns7$ cp  libjavaplugin_oji.so  ~/.mozilla/plugins
carlo@Laptop:/usr/lib/j2re1.5-sun/plugin/i386/ns7$

```

but STILL nothing in firefox!

---

### Post by taurus on 2006-12-07
What's the output of this command then?

```
ls -la ~/.mozilla/plugins
```

---

### Post by sp0nge on 2006-12-07
```
total 2232
drwxr-xr-x 2 carlo carlo    4096 2006-12-07 23:46 .
drwx------ 4 carlo carlo    4096 2006-09-13 19:42 ..
-rwxr-xr-x 1 carlo carlo     856 2006-11-13 10:53 flashplayer.xpt
-rwxr-xr-x 1 carlo carlo 2154768 2006-11-13 10:53 libflashplayer.so
-rw-r--r-- 1 carlo carlo  103432 2006-12-07 23:46 libjavaplugin_oji.so

```

---

### Post by taurus on 2006-12-08
And it's still no java support in firefox!!!  Maybe you already mentioned this in the previous posts but are you running firefox 1.5 or 2 (Dapper or Edgy)?

---

### Post by sp0nge on 2006-12-08
1.5 and Dapper.

---

### Post by sp0nge on 2006-12-08
Well, I've gone through 2 staff members now to no avail. I'm off to rest my head from this maddness for another night. I will continue to pary to the Ubuntu gods in hopes of a solution here, thanks to those who have helpped so far.

I'll check back in in about 12 hours or so

Long live Ubuntu (unless I kill the machine in which it rests)!

---

### Post by Perfect Storm on 2006-12-08
I think all the diffrent way to install java have "confused" and messed up Ubuntu to find Java. Perhaps cleaning and uninstall everything with java and its symblinks and copied files to start on a fresh java install afterwards.

On the bright side, sp0nge you have learned something you can use if we shall find a positive spot of this mess ;)

---

### Post by mlind on 2006-12-08
You can download sun-java5 source package from feisty repositories or Debian unstable, and rebuild it for your distribution. Debian unstable contains version 1.5.0-10-1 and builds & install fine for Edgy.

You can also use java-package to build binaries (.deb) from official source. You must download "Linux self-extracting file" instead of .rpm package.

---

### Post by sp0nge on 2006-12-08
Thanks for the input, mlind, but java is already installed. The problem here, is that I can NOT get firefox to recognize that fact...](*,)

---

### Post by mlind on 2006-12-08
> **sp0nge said:**
> Thanks for the input, mlind, but java is already installed. The problem here, is that I can NOT get firefox to recognize that fact...](*,)

The problem is probably what AI said, you currently have installed in way that Ubuntu doesn't like.

If you're using Ubuntu provided java packages, make sure you have installed **sun-java5-plugin** package.
And make sure alternatives are set correctly
```

sudo update-java-alternatives -s java-1.5.0-sun

```

If you installed java using other method, make sure you have symlink pointing to real libjavaplugin_oji.so in /usr/lib/mozilla/plugins and /usr/lib/mozialla-firefox/plugins folders.

Pointing firefox to url **about:plugins** should display if java is installed or not.

---

### Post by sp0nge on 2006-12-08
How do I make sure the symlink is pointing to the right place? I've tried to install via synaptic AND manually to no avail! To be honest, I've gone through so many steps I'm not sure where to go next.. any more details?

---

### Post by mlind on 2006-12-08
> **sp0nge said:**
> How do I make sure the symlink is pointing to the right place? I've tried to install via synaptic AND manually to no avail! To be honest, I've gone through so many steps I'm not sure where to go next.. any more details?

Remove manually installed jre's, then
```

sudo aptitude reinstall sun-java5-jre sun-java5-plugin
sudo update-java-alternatives -s java-1.5.0-sun

```

Check that symlinks are okay
```

$ ls -l /usr/lib/mozilla/plugins/libjavaplugin.so 
lrwxrwxrwx 1 root root 39 2006-12-08 15:37 /usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

$  ls -l /usr/lib/mozilla-firefox/plugins/libjavaplugin.so
lrwxrwxrwx 1 root root 39 2006-12-08 15:37 /usr/lib/mozilla-firefox/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

```

---

### Post by sp0nge on 2006-12-08
It returns 

```
bash: /etc/alternatives/mozilla-javaplugin.so: Permission denied

```

after the first line

---

### Post by mlind on 2006-12-08
> **sp0nge said:**
> It returns 

```
bash: /etc/alternatives/mozilla-javaplugin.so: Permission denied

```

after the first line

What command returs that output? Post the command and full output.

---

### Post by sp0nge on 2006-12-08
```
~$ ls -l /usr/lib/mozilla/plugins/libjavaplugin.so
lrwxrwxrwx 1 root root 39 2006-12-07 19:07 /usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
carlo@Laptop:~$ lrwxrwxrwx 1 root root 39 2006-12-08 15:37 /usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
bash: /etc/alternatives/mozilla-javaplugin.so: Permission denied

```

---

### Post by mlind on 2006-12-09
You're supposed to type only the ls -commands, and see if the output is a valid symlink

---

