---
title: "firefox java plugin doesn't work."
date: 2007-08-10
forum: General Help
---

### Post by band-aid on 2007-08-10
I am trying to get the firefox java plugin to install as per the instructions on the internet. I went to a site with a java applet and clicked where the applet was to install the missing plugin. No plugin was found so I had to do a manual install. I downloaded the self extracting bin file, made it executable, and ran it inside  /usr/local. I then made the simlink from the plugin .so file in the java installation folder to the firefox plugins folder at /usr/lib/firefox/plugins. Now when I go to a site with a java applet, it does not say that the plugin is missing, but the applet does not start. What have I missed?

---

### Post by capink on 2007-08-10
This is how I enabled java. I hope this would help:

1. Install java, the plugin and the fonts

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2. Create a symlink in the firefox plugins directory

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

3.Enable Java in firefox

goto > Edit > Preferences > Content > Enable java

---

### Post by punkrokk on 2007-08-11
great thread, why isnt' it always this easy :)

---

### Post by jspangler on 2007-08-11
Thanks for answering my question too!

---

### Post by band-aid on 2007-08-11
looks like your everyone's hero today, mines working great now!

---

### Post by aeronori on 2007-08-19
Hi all,

I have also started using Ubuntu just 2 days ago...

I have installed the Sun version 1.6 and also checked in the firefox by typing about:plugins in the browser. It seems to be updated there. I have also made the "Sun" as the default browser. I also have the IBM Blackdown 1.4.2. 

Inspite of this, I am unable to run two windows with Java script. I generally listen to songs online and in some sites we can make our own  playlist and then we "play", "stop", "pause" , "skip one song back" or "skip on song forward" . So the problem is that even though these buttons are visible in the java-window, some of the buttons are not operational.  I did not find any issues with this website in windows...

can you help me in fixing this problem.?

For eg...you can take the website [http://www.raaga.com/channels/worldmusic/movie/WM00037.html](http://www.raaga.com/channels/worldmusic/movie/WM00037.html) and select all the songs and play it. then u get a player which starts playing the songs but we cannot skip a song either backward or forward ....

thanks for ur help...

---

### Post by toddpedlar on 2007-08-21
> **capink said:**
> This is how I enabled java. I hope this would help:

1. Install java, the plugin and the fonts

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2. Create a symlink in the firefox plugins directory

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

3.Enable Java in firefox

goto > Edit > Preferences > Content > Enable java

Okay, I've done exactly this, but can't get the browser to recognize that the plugin is installed.  There are two things that perhaps differ from the situation of others who have found this to work.

1) I'm running the swiftfox version of firefox - can that make any difference?
2) I have both a libjavaplugin.so and the libjavaplugin_oji.so symlinks in my /usr/lib/firefox/plugins directory.

Help?

---

### Post by toddpedlar on 2007-08-21
> **toddpedlar said:**
> Okay, I've done exactly this, but can't get the browser to recognize that the plugin is installed.  There are two things that perhaps differ from the situation of others who have found this to work.

1) I'm running the swiftfox version of firefox - can that make any difference?
2) I have both a libjavaplugin.so and the libjavaplugin_oji.so symlinks in my /usr/lib/firefox/plugins directory.

Help?

Neeeeeevvvvvver mind....

It was option 1... softlink into the /opt/swiftfox/plugins directory made it work like a charm.

t

---

### Post by giox on 2007-09-26
I did all the steps above but my browser still ask me to download the plugin for java. I have no idea what else i can do. If this matter I update the firefox to 2.0.0.7 yesterday.

---

### Post by capink on 2007-09-26
Are you using ubuntu firefox (updated from ubuntu repositories) or mozilla binaries? Was java working alright before the update?

---

### Post by giox on 2007-09-27
I used binaries from the mozilla page. And I am not sure if it works cuz I just reinstall everything cuz a problem with my ATI card. But I am able to install the flash plugin and others but not the java for some reason.

 ~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

### Post by capink on 2007-09-27
> **giox said:**
> I used binaries from the mozilla page. And I am not sure if it works cuz I just reinstall everything cuz a problem with my ATI card. But I am able to install the flash plugin and others but not the java for some reason.

 ~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

The binaries from mozilla does not recognize the directory /usr/lib/firefox/plugins unless you make it so by sym links. It instead reads /path/mozilla/firefox/plugins. So if you copied the mozilla binaries top /opt the plugins directory would be /opt/firefox/plugins. So you have two options:

A. modify step three in this thread to:

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so [COLOR="Red"]/path/to/mozilla/firefox[/COLOR]/plugins
```

B. Move the plugins directory to /usr/lib/firefox/plugins to make it compatible with any plugins in the repositories.

```
sudo mv /path/to/mozilla/firefox/plugins /path/to/mozilla/firefox/plugins_bak
sudo ln -s /usr/lib/firefox/plugins /path/to/mozilla/firefox
```

Note that you will have to reinstall all the plugins to the new location  in /usr/lib/firefox/plugins

---

### Post by crunchfighter on 2007-12-27
Capink,
Thanks for the help on this.  I used your steps on your initial post on this thread and it worked, once I installed the plug-in as well.

For those that follow - 

Enter the two lines of code capink has on post #2 of this thread.
Enable java in firefox.
go to [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp) and click on verify installation
install the plug-in that says java6 (not the ones that say gcj or java5!)

Thanks.

---

### Post by seamouse on 2008-01-03
Changing 'java-6-sun-1.6.0.00' to 'java-6-sun' in the link works better if you ever plan to update the java-6 install.

```

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

---

### Post by jespdj on 2008-01-04
And note that this is not going to work if you are using the 64-bit version of Ubuntu, because Sun has no 64-bit version of the Java browser plug-in (at least not for Java 6 or older).

---

