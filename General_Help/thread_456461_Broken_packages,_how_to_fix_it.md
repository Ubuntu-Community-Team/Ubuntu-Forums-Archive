---
title: "Broken packages, how to fix it?"
date: 2007-05-27
forum: General Help
---

### Post by vincent.vega on 2007-05-27
Hey guys!

I am getting some messages about broken packages, besides that k3b simply stopped working (not going past the splash screen).

Since everything was running fine a few days ago and I haven't installed any new software, this was probably caused by one of the updates.

Output of [FONT="Fixedsys"]sudo aptitude install[/FONT]:
```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are BROKEN:
  avidemux gstreamer0.10-plugins-bad jackd kdelibs4c2a libavcodec0d 
  libk3b2-mp3 libswfdec0.3 mjpegtools netbeans5.5 netbeans5.5-platform 
  openoffice.org-writer vlc-nox 
The following packages will be REMOVED:
  ant-optional aspell-pt-br azureus beneath-a-steel-sky cabextract cups-pdf 
  fastjar flashplugin-nonfree flight-of-the-amazon-queen gmountiso 
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly java-common 
  java-gcj-compat junit ladcca2 lbreakout2 lbreakout2-data liba52-0.7.4 
  libbcel-java libbcprov-java libcairo-java libcommons-beanutils-java 
  libcommons-cli-java libcommons-collections-java 
  libcommons-collections3-java libcommons-dbcp-java 
  libcommons-digester-java libcommons-el-java libcommons-launcher-java 
  libcommons-logging-java libcommons-modeler-java libcommons-pool-java 
  libdvdread3 libfaac0 libfaad2-0 libfluidsynth1 libfreebob0 libgcj7-jar 
  libglib-java libgnucrypto-java libgpgme11 libgtk-java libgtk-jni 
  libid3tag0 libjack0.100.0-0 libjsch-java liblog4j1.2-java libltdl3 
  liblua50 liblualib50 liblucene-java liblucene-java-doc libmad0 
  libmjpegtools0c2a libmp4v2-0 libmpeg2-4 libmx4j-java libquicktime0 
  libregexp-java libsdl-mixer1.2 libseda-java libservlet2.4-java 
  libsidplay1 libsmpeg0 libswt3.2-gtk-java libswt3.2-gtk-jni 
  libtomcat5.5-java libwps-0.1-1 libxvidcore4 ltris msttcorefonts ntp 
  odbcinst1debian1 openoffice.org-help-en-gb openoffice.org-l10n-en-us 
  sbackup scummvm seahorse sun-java6-bin sun-java6-jdk sun-java6-jre 
  sun-java6-plugin unixodbc 
0 packages upgraded, 0 newly installed, 84 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 362MB will be freed.
The following packages have unmet dependencies:
  kdelibs4c2a: Depends: liblua50 (>= 5.0.3) but it is not installable
               Depends: liblualib50 (>= 5.0.3) but it is not installable
  openoffice.org-writer: Depends: libwps-0.1-1 but it is not installable
  libswfdec0.3: Depends: libmad0 (>= 0.15.1b) but it is not installable
  avidemux: Depends: libfaac0 (>= 1.24clean) but it is not installable
            Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
            Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
  vlc-nox: Depends: liba52-0.7.4 but it is not installable
           Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libid3tag0 (>= 0.15.1b) but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpeg2-4 but it is not installable
  netbeans5.5: Depends: sun-java5-jdk but it is not installable or
                        sun-java6-jdk but it is not installable
  gstreamer0.10-plugins-bad: Depends: libjack0.100.0-0 (>= 0.102.20) but it is not installable
  netbeans5.5-platform: Depends: sun-java5-jre but it is not installable or
                                 sun-java6-jre but it is not installable
  libavcodec0d: Depends: liba52-0.7.4 but it is not installable
  mjpegtools: Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
              Depends: libquicktime0 but it is not installable
  jackd: Depends: libjack0.100.0-0 (= 0.102.20-1) but it is not installable
  libk3b2-mp3: Depends: libmad0 (>= 0.15.1b) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
mjpegtools

Keep the following packages at their current version:
ant-optional [1.6.5-6build1 (feisty, now)]
java-common [0.25ubuntu2 (feisty, now)]
liba52-0.7.4 [0.7.4-7 (feisty, now)]
libdvdread3 [0.9.7-2ubuntu1 (feisty, now)]
libfaac0 [1.24clean-0ubuntu4 (feisty, now)]
libfaad2-0 [2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 (feisty, now)]
libfreebob0 [1.0.0-3 (feisty, now)]
libgcj7-jar [4.1.2-0ubuntu5 (feisty, now)]
libid3tag0 [0.15.1b-8 (feisty, now)]
libjack0.100.0-0 [0.102.20-1 (feisty, now)]
libltdl3 [1.5.22-4 (feisty, now)]
liblua50 [5.0.3-2build1 (feisty, now)]
liblualib50 [5.0.3-2build1 (feisty, now)]
libmad0 [0.15.1b-2.1 (feisty, now)]
libmp4v2-0 [2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 (feisty, now)]
libmpeg2-4 [0.4.1-1 (feisty, now)]
libwps-0.1-1 [0.1~svn20070131-2build1 (feisty, now)]
libxvidcore4 [2:1.1.2-0.1ubuntu1 (feisty, now)]
odbcinst1debian1 [2.2.11-13 (feisty, now)]
sun-java6-bin [6-00-2ubuntu2 (feisty, now)]
sun-java6-jdk [6-00-2ubuntu2 (feisty, now)]
sun-java6-jre [6-00-2ubuntu2 (feisty, now)]
unixodbc [2.2.11-13 (feisty, now)]

Leave the following dependencies unresolved:
rhythmbox recommends gstreamer0.10-plugins-ugly
banshee recommends gstreamer0.10-plugins-ugly
avidemux recommends mjpegtools
Score is -1668

Accept this solution? [Y/n/q/?] 
```

How can I fix this?

---

### Post by Bakerman on 2007-05-28
Hi, I don't know if this would be related to your problem, but in the Synaptic Package Manager there is an option to 'fix broken packages'. You can find it in the edit section.

---

### Post by trippinnik on 2007-05-28
Do you sometimes use aptitude and sometimes use Synaptic?  I've noticed that this can be troublesome as you have a large number of packages that are marked to be removed (but you may not really want them removed).  anyway one way to fix broken packages is 
sudo aptitude -f

---

### Post by trippinnik on 2007-05-28
looks like that is not such a good idea! scratch that.  it'll probably remove way too many packages.  apt-get has some package fixing tools too.  try apt-get --help

---

### Post by vincent.vega on 2007-05-28
> **Bakerman said:**
> Hi, I don't know if this would be related to your problem, but in the Synaptic Package Manager there is an option to 'fix broken packages'. You can find it in the edit section.

This option didn't do anything for me. Before using it I checked synaptic's broken package filter and to my surprise it didn't list any package as broken! :confused:

> **trippinnik said:**
> Do you sometimes use aptitude and sometimes use Synaptic?  I've noticed that this can be troublesome as you have a large number of packages that are marked to be removed (but you may not really want them removed).  anyway one way to fix broken packages is 
sudo aptitude -f

Yes, sometimes I use Synaptic and some times a use aptitude. I didn't know this could cause problems :/

The funny thing is that except for k3b everything seems to be working fine, since I've updated my system successfully using the update manager today and Synaptic is not listing any broken package.

---

### Post by trippinnik on 2007-06-02
I've actually run the aptitude fix packages now.  It took quite a while, but actually didn't remove anything I needed.  I've read on the forums before that Synaptic and aptitude don't communicate with each other, which results in the different reporting.  I'm not sure it's actually a problem, but at one point in the past aptitude wanted to remove amarok from my system as an unused app everytime i tried to upgrade.  Have you tried to purge K3B? Maybe some others have more info about the aptitude/syanptic situation.

---

### Post by bapoumba on 2007-06-02
> **trippinnik said:**
> IMaybe some others have more info about the aptitude/syanptic situation.
Unless I am mistaken (and please someone correct me here) , it comes from the logs files.
apt-get relies on dpkg's log. Synaptic only logs history (> File > History) and aptitude has its own log in /var/lib/aptitude/pkgstates. If you use one or the other, alternatively, logs will be incomplete (and hence dependencies requirements) ending up with aptitude suggesting removing needed packages.
I've been using aptitude exclusively for that reason (now the autoremove option in apt-get has somewhat filled the dependency handling gap between the two).

Long time ago, I got caught in this dependency problem, and I could update aptitude's log without installing/reinstalling packages. I've been looking for the way I did that (I think it was from aptitude interface) for some time now. May be "mark as manually installed".  Anyone ?

---

### Post by ricardisimo on 2007-06-04
I'm not sure how vincent.vega did it, but I'm looking at almost exactly the same messages because I tried updating k3b to the unstable 1.01 version. Lesson learned. Help would be greatly appreciated.

I currently have 30 broken packages on my system (almost all KDE apps), and if I ask Synaptic to reinstall, it tells me that it will entail removing - basically - my entire system. I don't quite get all of the dependency logic, but it seems a bit extreme to demand this because of one poorly-installed CD-burning app.

---

### Post by ricardisimo on 2007-06-04
That was quick. Thank you, aptitude.

```
sudo aptitude remove k3b
```resolved all problems. Now I'll just reinstall k3b from the stable repos and we should be done. I'm curious to see what happens with many of the dependencies from the failed k3b upgrade that did not leave with k3b:  ```
libacl1 libattr1 libdbus-qt-1-1c2 libexpat1 libidn11 libjpeg62 libx11-6 libxext6 libxi6 libxinerama1 
```
Will I still need them for other things? We'll see.

---

