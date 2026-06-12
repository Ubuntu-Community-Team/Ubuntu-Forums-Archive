---
title: "alternatives to Catfish File Search?"
date: 2021-06-16
forum: General Help
---

### Post by ardouronerous on 2021-06-16
I'm running Xubuntu 20.04.

[ATTACH=CONFIG]288667[/ATTACH]

Catfish File Search has been becoming unresponsive and crashing, sometimes it works, but most of the time it crashes. Are there alternatives available in the Ubuntu repos or a snap or flatpak? I'm looking for a GUI-based alternative. I would like to avoid PPAs as much as possible.

Thank you.

---

### Post by dragonfly41 on 2021-06-16
searchmonkey (gui)

---

### Post by dddman on 2021-06-16
Catfish is just a GUI for the "find" command.  I would think a reinstall would fix that.

---

### Post by ActionParsnip on 2021-06-16
locate command in the terminal

---

### Post by TheFu on 2021-06-16
recoll  [https://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll](https://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll)  I use the Canonical repo version. Works great.
beagle [https://www.linux.com/news/efficient-desktop-searching-beagle/](https://www.linux.com/news/efficient-desktop-searching-beagle/)  

It think those index not just the filenames, but also the contents.  I know **recoll** does. I use it perhaps 20x daily.
I also use **locate**  many times daily. Locate only knows filenames, not what is inside.
I've never used beagle, but it was the default for some Ubuntu DEs.

---

### Post by ardouronerous on 2021-06-16
> **dragonfly41 said:**
> searchmonkey (gui)

I installed it, but it didn't function as I would hoped though, like when I did a search, it did find the file, but when I tried to click on the file from the search window, it didn't open the file and going to the file's folder location, it didn't open my file manager. Also, there's no option to copy the file to another location.

> **TheFu said:**
> recoll [https://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll](https://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll) I use the Canonical repo version. Works great.
beagle [https://www.linux.com/news/efficient-desktop-searching-beagle/](https://www.linux.com/news/efficient-desktop-searching-beagle/)

It think those index not just the filenames, but also the contents. I know recoll does. I use it perhaps 20x daily.
I also use locate many times daily. Locate only knows filenames, not what is inside.
I've never used beagle, but it was the default for some Ubuntu DEs.

Recoll was taking too long in indexing my file system, I just gave up after that. And Beagle's dependencies are too much:

```
sudo apt-get --no-install-recommends install beagle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ant ant-optional ca-certificates-java default-jre default-jre-headless
  java-common libactivation-java libaopalliance-java libapache-pom-java
  libargs4j-java libatinject-jsr330-api-java libcdi-api-java libcodemodel-java
  libcommons-cli-java libcommons-codec-java libcommons-compress-java
  libcommons-io-java libcommons-jexl2-java libcommons-lang3-java
  libcommons-logging-java libcommons-parent-java libdom4j-java
  libdtd-parser-java libfastinfoset-java libgeronimo-annotation-1.3-spec-java
  libgeronimo-interceptor-3.0-spec-java libguava-java libguice-java
  libhtsjdk-java libhttpclient-java libhttpcore-java libistack-commons-java
  libjaxb-api-java libjaxb-java libjaxen-java libjsoup-java libjsr305-java
  libmaven-file-management-java libmaven-parent-java libmaven-resolver-java
  libmaven-shared-io-java libmaven-shared-utils-java libmaven3-core-java
  libngs-java libngs-sdk-dev libngs-sdk2 libplexus-archiver-java
  libplexus-cipher-java libplexus-classworlds-java
  libplexus-component-annotations-java libplexus-interpolation-java
  libplexus-io-java libplexus-sec-dispatcher-java libplexus-utils2-java
  librelaxng-datatype-java librngom-java libsisu-guice-java
  libsisu-inject-java libsisu-ioc-java libsisu-plexus-java libslf4j-java
  libsnappy-java libsnappy-jni libstax-ex-java libstreambuffer-java
  libtxw2-java libwagon-http-java libwagon-provider-api-java
  libxml-commons-resolver1.1-java libxsom-java libxz-java openjdk-11-jre
  openjdk-11-jre-headless
Suggested packages:
  ant-doc default-jdk | java-compiler | java-sdk antlr javacc junit junit4
  jython libbcel-java libbsf-java libcommons-net-java libmail-java
  libjaxp1.3-java libjdepend-java libjsch-java liblog4j1.2-java liboro-java
  libregexp-java libxalan2-java beagle-doc libaopalliance-java-doc
  libatinject-jsr330-api-java-doc libservlet3.1-java libcommons-io-java-doc
  libcommons-jexl2-java-doc libcommons-lang3-java-doc libavalon-framework-java
  libcommons-logging-java-doc libexcalibur-logkit-java libdom4j-java-doc
  libmsv-java libxpp2-java libxpp3-java libdtd-parser-java-doc libasm-java
  libcglib-java picard-tools libjdom1-java libxom-java libjsoup-java-doc
  libjsr305-java-doc libmaven-file-management-java-doc
  libmaven-shared-io-java-doc libmaven-shared-utils-java-doc liblogback-java
  libplexus-cipher-java-doc libplexus-classworlds-java-doc
  libplexus-sec-dispatcher-java-doc libplexus-utils2-java-doc testng
  libosgi-compendium-java libosgi-core-java
  libxml-commons-resolver1.1-java-doc fonts-dejavu-extra fonts-ipafont-gothic
  fonts-ipafont-mincho fonts-wqy-microhei | fonts-wqy-zenhei
Recommended packages:
  libjansi-java libasm-java libcglib-java libatk-wrapper-java-jni
  fonts-dejavu-extra
The following NEW packages will be installed:
  ant ant-optional beagle ca-certificates-java default-jre
  default-jre-headless java-common libactivation-java libaopalliance-java
  libapache-pom-java libargs4j-java libatinject-jsr330-api-java
  libcdi-api-java libcodemodel-java libcommons-cli-java libcommons-codec-java
  libcommons-compress-java libcommons-io-java libcommons-jexl2-java
  libcommons-lang3-java libcommons-logging-java libcommons-parent-java
  libdom4j-java libdtd-parser-java libfastinfoset-java
  libgeronimo-annotation-1.3-spec-java libgeronimo-interceptor-3.0-spec-java
  libguava-java libguice-java libhtsjdk-java libhttpclient-java
  libhttpcore-java libistack-commons-java libjaxb-api-java libjaxb-java
  libjaxen-java libjsoup-java libjsr305-java libmaven-file-management-java
  libmaven-parent-java libmaven-resolver-java libmaven-shared-io-java
  libmaven-shared-utils-java libmaven3-core-java libngs-java libngs-sdk-dev
  libngs-sdk2 libplexus-archiver-java libplexus-cipher-java
  libplexus-classworlds-java libplexus-component-annotations-java
  libplexus-interpolation-java libplexus-io-java libplexus-sec-dispatcher-java
  libplexus-utils2-java librelaxng-datatype-java librngom-java
  libsisu-guice-java libsisu-inject-java libsisu-ioc-java libsisu-plexus-java
  libslf4j-java libsnappy-java libsnappy-jni libstax-ex-java
  libstreambuffer-java libtxw2-java libwagon-http-java
  libwagon-provider-api-java libxml-commons-resolver1.1-java libxsom-java
  libxz-java openjdk-11-jre openjdk-11-jre-headless
0 upgraded, 74 newly installed, 0 to remove and 12 not upgraded.
Need to get 58.9 MB of archives.
After this operation, 203 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

> **dddman said:**
> Catfish is just a GUI for the "find" command. I would think a reinstall would fix that.

I went to Synaptic Package Manager and reinstalled Catfish, it didn't help, I still get that unresponsive message. Is there a way to report this issue with Catfish to it's developers? I prefer it to the alternatives.

---

### Post by &amp;KyT$0P# on 2021-06-16
> **ardouronerous said:**
> I prefer it to the alternatives.

I haven't tested this myself, but can you build [this newer version of Catfish]("https://packages.ubuntu.com/source/hirsute/catfish") from source on your 20.04 and install the .deb package you generate?  If so does that version run ok?

---

### Post by dddman on 2021-06-16
There is a ask a "ask a question" option at launchpad.
[https://bugs.launchpad.net/ubuntu/+source/catfish](https://bugs.launchpad.net/ubuntu/+source/catfish)

Angrysearch sounds like a good alternative, maybe give it a try.
[https://itsfoss.com/angrysearch/](https://itsfoss.com/angrysearch/)

---

### Post by ardouronerous on 2021-06-16
> **halogen2 said:**
> I haven't tested this myself, but can you build [this newer version of Catfish]("https://packages.ubuntu.com/source/hirsute/catfish") from source on your 20.04 and install the .deb package you generate?  If so does that version run ok?

I have no experiencing in building software from source. But thanks anyway.

> **dddman said:**
> There is a ask a "ask a question" option at launchpad.
[https://bugs.launchpad.net/ubuntu/+source/catfish](https://bugs.launchpad.net/ubuntu/+source/catfish)

Thanks, I'll try to message the devs.

> Angrysearch sounds like a good alternative, maybe give it a try.
[https://itsfoss.com/angrysearch/](https://itsfoss.com/angrysearch/)

Angrysearch sounds like Recoll where it has to index my file system, which took a long time I just gave up on it and the install process is kinda scary, because I don't have much experience in installing software that way.

Looks like I'll have to live with a glitchy catfish though.

---

### Post by TheFu on 2021-06-16
> **ardouronerous said:**
> Recoll was taking too long in indexing my file system, I just gave up after that. And Beagle's dependencies are too much:

I feel your pain.  The first Recoll index takes hours, but only touched files get handled going forward. Plus, you can schedule when you'd like the recoll to index. It isn't automatic. Here's my crontab for reindexing recoll daily, while I'm still sleeping:
```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR # sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
10 4 * * * export RECOLL_CONFDIR=/d/D2/recoll-index/recoll ; nice /usr/bin/recollindex > /dev/null 2>&1

```
That's for 34TB of stuff, mostly old TV shows.  The recoll index uses .... 2.1GB. Searches are nearly instantaneous and the "sounds-like" results are great when spelling isn't perfect. 1000000x better than 'find', if the index isn't too out of date.  Even updating the locate/updatedb takes some time on that system.
```
$ time sudo updatedb

real    3m20.583s
user    0m3.860s
sys     0m13.608s
```

If I saw those beagle dependencies - I'd have rejected it too! ;)

I have a script that wraps both **locate** and **recoll** queries to make my life easier.  I find the Recoll GUI too cumbersome, but I find most GUIs too cumbersome.  Give me a shell where I'm 100x more efficient than some GUI.

---

### Post by dddman on 2021-06-17
Mate-search-tool

**No** indexing required and its fast.  Should work on xubuntu, I installed it on my ubuntu.  The mate utility package is required.

*sudo apt install mate-utils*

I'm guessing it will show up in your menu or your menu editor  If not, use the terminal command:

*mate-search-tool*

To bring it up and add it to your launcher.

[ATTACH=CONFIG]288670[/ATTACH]

---

### Post by ardouronerous on 2021-06-17
> **dddman said:**
> Mate-search-tool

**No** indexing required and its fast.  Should work on xubuntu, I installed it on my ubuntu.  The mate utility package is required.

*sudo apt install mate-utils*

I'm guessing it will show up in your menu or your menu editor  If not, use the terminal command:

*mate-search-tool*

To bring it up and add it to your launcher.

[ATTACH=CONFIG]288670[/ATTACH]

Thanks, it's better than the other alternatives and it works fast, no indexing, so finding documents with this will be as easy as Catfish, even though I still prefer it over this, I'll be using this for the time being, so thanks.

I've reported the Catfish bug here: [https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/1932240](https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/1932240)

---

### Post by dragonfly41 on 2021-06-17
I feel that you did not give SearchMonkey a good workout. I must reply even though you have found a satisfactory solution.

I launch SearchMonkey and I see a rich set of search parameters (including Regexp).

by name
by content
by size
by date

Regarding your observations


> like when I did a search, it did find the file, but when I tried to click on the file from the search window, it didn't open the file and going to the file's folder location, it didn't open my file manager. Also, there's no option to copy the file to another location.


Settings > Configuration > Default Applications

allows 
Default text editor - e.g. Geany
Default folder explorer - e.g. Thunar (is your File Explorer here?)
Default web browser - e.g. Chromium

On your point about "no option to copy the file to another location" (not raised in first post) this is achieved in one of several ways:

Right click on selected file to choose:

1. Edit (File) - which launches the file in Geany where it can be edited and saved.
2. Copy (Filename) - which places the absolute filepath into clipboard and then you can use this in a terminal command
3. Explore Folder - which launches the file in Thunar (or other Explorer).


In summary I don't think that you explored Settings in full.

However I do use other search methods from time to time including bespoke python script.  And also the Locate python extension in Albert (a very useful tool for multiple uses).

Because I often shuffle around project folders frequently in development desktop, tools such as Recoll require reindexing.

Another fast search tool (name and content) is ripgrep.   

Horses for courses.

---

