---
title: "Java can't run applets in Firefox ==&gt; no hushmail"
date: 2008-06-11
forum: General Help
---

### Post by Niels Olson on 2008-06-11
I don't know java from coffee, but here are my notes thus far:

This is not new. I don't think I've ever gotten hushmail to work in Ubuntu.

edit: this only applies to the java applet method, which can be forced by using this url: [https://www.hushmail.com/java](https://www.hushmail.com/java)

Something similar, related to Hush in Firefox under Hardy Heron, has been reported in Ubuntu's bug tracker; the author attributes the problem to the GNU Java Compiler, but I'm not sure I buy that, since I have the same issue with Sun Java: [https://bugs.launchpad.net/ubuntu/+source/gcj-4.2/+bug/200236](https://bugs.launchpad.net/ubuntu/+source/gcj-4.2/+bug/200236)

Hush works in Opera under Ubuntu Hardy Heron after setting the java path to /usr/lib/jvm/java-6-sun/jre/lib/i386, however, there is no libjavaplugin_oji.so in this path.

In Firefox 3.0 under Hardy Heron, in the menu Edit -> Preferences -> Content, Java *IS* enabled (so is javascript)
In Firefox 3.0 under Hardy Heron, in the menu Tools -> Add ons -> Plugins, the plugin Java(TM) Plug-in 1.6.0_06-b02 is installed
In Firefox 3.0 under Hardy Heron, in the menu Tools -> Add ons -> Extensions, the  Java Console 6.0.02 is installed and enabled

I have set the following symlinks
/usr/lib/firefox-3.0/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox-addons/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so

A visit in Firefox 3.0 under Hardy Heron to [http://javatester.org/version.html](http://javatester.org/version.html) shows I'm running Java Version 1.6.0 from Sun Microsystems
A visit in Firefox 3.0 under Hardy Heron to [http://javatester.org/enabled.html](http://javatester.org/enabled.html) shows the browser can indeed run applets according to the <applet> tag, but not according to the javascript methods.
A visit in Firefox 3.0 under Hardy Heron to [http://java.com/en/download/help/testvm.xml?ff3](http://java.com/en/download/help/testvm.xml?ff3) shows the browser cannot run applets. The status bar shows the following messages in order: "starting applet" "Applet loaded" "Start: applet not initialized"

A visit in Firefox 3.0 under Hardy Heron to ```
about:plugins
``` shows these java plugins:
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 	
	Yes
application/x-java-applet 	Java 	
	Yes
application/x-java-applet;version=1.1 	Java 	
	Yes
application/x-java-applet;version=1.1.1 	Java 	
	Yes
application/x-java-applet;version=1.1.2 	Java 	
	Yes
application/x-java-applet;version=1.1.3 	Java 	
	Yes
application/x-java-applet;version=1.2 	Java 	
	Yes
application/x-java-applet;version=1.2.1 	Java 	
	Yes
application/x-java-applet;version=1.2.2 	Java 	
	Yes
application/x-java-applet;version=1.3 	Java 	
	Yes
application/x-java-applet;version=1.3.1 	Java 	
	Yes
application/x-java-applet;version=1.4 	Java 	
	Yes
application/x-java-applet;version=1.4.1 	Java 	
	Yes
application/x-java-applet;version=1.4.2 	Java 	
	Yes
application/x-java-applet;version=1.5 	Java 	
	Yes
application/x-java-applet;version=1.6 	Java 	
	Yes
application/x-java-applet;jpi-version=1.6.0_06 	Java 	
	Yes
application/x-java-bean 	Java 	
	Yes
application/x-java-bean;version=1.1 	Java 	
	Yes
application/x-java-bean;version=1.1.1 	Java 	
	Yes
application/x-java-bean;version=1.1.2 	Java 	
	Yes
application/x-java-bean;version=1.1.3 	Java 	
	Yes
application/x-java-bean;version=1.2 	Java 	
	Yes
application/x-java-bean;version=1.2.1 	Java 	
	Yes
application/x-java-bean;version=1.2.2 	Java 	
	Yes
application/x-java-bean;version=1.3 	Java 	
	Yes
application/x-java-bean;version=1.3.1 	Java 	
	Yes
application/x-java-bean;version=1.4 	Java 	
	Yes
application/x-java-bean;version=1.4.1 	Java 	
	Yes
application/x-java-bean;version=1.4.2 	Java 	
	Yes
application/x-java-bean;version=1.5 	Java 	
	Yes
application/x-java-bean;version=1.6 	Java 	
	Yes
application/x-java-bean;jpi-version=1.6.0_06 	Java 	
	Yes

---

### Post by jimv on 2008-06-11
It must not like you.  I just created an account and sent myself an email.

Using Ubuntu Hardy with sun-java6-jre installed.

---

### Post by Niels Olson on 2008-06-11
> **jimv said:**
> It must not like you.  I just created an account and sent myself an email.

Using Ubuntu Hardy with sun-java6-jre installed.

Ah, Hush uses two methods: the only end-to-end transfer method is to use the onboard java applet. The method you used ships the data back to Hush's servers and encrypts it there. This is the method that allowed the US government to force Hush to disclose a hush user's emails. If that person had used the java applet, Hush could have never intercepted an unencrypted copy of his mail.

Try it from here [https://www.hushmail.com/java](https://www.hushmail.com/java)

---

### Post by jimv on 2008-06-11
Ok ok, so it turns out that my Java was broke too.  I just tried to load a few java apps and they got stuck on the "starting applet" part.

BUT

I fixed it.  I removed all the sun java stuff.  Then I got rid of all the openjdk stuff.  Then I reinstalled sun java and the plugin, and updated the java alternatives.

```

sudo apt-get remove sun-java*
sudo apt-get remove openjdk*
sudo apt-get autoremove
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```


I just logged in with that link and it worked.

---

### Post by yman on 2008-06-11
So shouldn't this thread be marked as solved?

---

### Post by jimv on 2008-06-11
> **yman said:**
> So shouldn't this thread be marked as solved?

If what I proposed as a fix works for the OP, then I suppose it will be marked as solved.

---

### Post by Niels Olson on 2008-06-11
> **jimv said:**
> If what I proposed as a fix works for the OP, then I suppose it will be marked as solved.

That worked. Now, that said . . .

these packages that depend on openjdk are removed
```
Removing azureus ...
Removing icedtea-gcjwebplugin ...
Removing libcommons-cli-java ...
Removing libcommons-lang-java ...
Removing liblog4j1.2-java ...
Removing openjdk-6-jre ...
Removing openjdk-6-jre-headless ...
Removing openjdk-6-jre-lib ...
```

There are also a bunch of packages it recommends installing when you reinstall, so you might want to copy those down.

You will also have to restart firefox. If you don't, that's fine, it will crash, and then you'll restart :P

As for, is it resolved? Well, reinstalling Java seems like a pretty big hammer to throw at the problem, and the fact that applets don't run without that seems like a pretty big problem, yet Firefox, Sun Java, and Hush all seem to be square. So does that make it a candidate to be a bug for the distro?

---

### Post by jimv on 2008-06-11
It does seem like a bug.  I couldn't load any java applets (funny that I never noticed) at all. I think that it might have been looking for one of the openjdk packages...but I have no idea.  I'm also hoping that removing those doesn't mess up anything else; I guess I'll have to wait and see.

---

### Post by yman on 2008-06-13
I only noticed today that I too can't load Java applets. Now I need to read this thread carefully. How annoying.

Actually, [this]("http://streaming.linux-magazin.de/events/linuxtag08/archive/aseigo/frames-java.htm") applet starts, but immediately gets stuck.

---

### Post by yman on 2008-06-16
Now Netbeans won't install. Whatever this fix did, it broke something else.

```
yman@hardy:~$ sudo apt-get install netbeans
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  netbeans: Depends: libnb-apisupport1-java (>= 6.0.1) but it is not going to be installed
            Depends: libnb-ide8-java (>= 6.0.1) but it is not going to be installed
            Depends: libnb-java1-java (>= 6.0.1) but it is not going to be installed
E: Broken packages
```

---

### Post by efguerre on 2008-11-07
> **jimv said:**
> Ok ok, so it turns out that my Java was broke too.  I just tried to load a few java apps and they got stuck on the "starting applet" part.

BUT

I fixed it.  I removed all the sun java stuff.  Then I got rid of all the openjdk stuff.  Then I reinstalled sun java and the plugin, and updated the java alternatives.

```

sudo apt-get remove sun-java*
sudo apt-get remove openjdk*
sudo apt-get autoremove
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```


I just logged in with that link and it worked.

Thx :guitar:

---

