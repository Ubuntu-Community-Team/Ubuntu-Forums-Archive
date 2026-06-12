---
title: "Java isn't working in Firefox"
date: 2008-05-03
forum: General Help
---

### Post by BWF89 on 2008-05-03
I was trying to view the material on [this website]("http://services.alphaworks.ibm.com/manyeyes/view/S62J0EQ9mVa6O_kEoi71E2~") and it said I needed Java Runtime Environment. I uninstalled the open source implementation of Java that the Kubuntu extras package installed and installed the following official Java packages:

sun-java6-bin
sun-java6-doc
sun-java6-fonts
sun-java-jre
sun-java6-plugin

Than I was looking at the readout on Adept and saw there was a problem with the sun-java6-doc so I uninstalled it and reinstalled all of the other files. They all reinstalled successfully. But still when I go into Firefox to view something that needs Java it doesn't work.

---

### Post by priegog on 2008-05-03
I also have this problem. I hadn't noticed because I hadn't browsed to a site that needed Java up until today. Any solutions?

---

### Post by Zorael on 2008-05-03
sun-java6-doc requires that you download the documentation yourself and place the zip in /tmp to successfully install.

Anyway, I'm not sure what to say, it worked without hitches for me. You could try to reinstall the restricted extras package.
```
$ sudo aptitude reinstall kubuntu-restricted-extras sun-java6-jre
```

---

### Post by priegog on 2008-05-03
already tried that :S
I've also tried doing the sudo update-alternatives --config java  and selecting different versions.
Oh, and installing the plugin from within firefox. No luck. 
If this is as widespread as it seems to be, why is it not  big deal? or am I the only loseR?

---

### Post by Zorael on 2008-05-03
I'm not sure if it's relevant, but have you set it to be the default java engine?
```
$ sudo update-alternatives --config java
```
Then pick OpenJava or Sun's.

---

### Post by priegog on 2008-05-03
haha beat you to it in the edit

---

### Post by stevoo on 2008-05-03
i may be wrong 

but Sun has developed a plugin that will be working with the new firefox to improve performance. That is why you do not see the java not installed. Try googling for that

---

### Post by BWF89 on 2008-05-03
> **Zorael said:**
> Anyway, I'm not sure what to say, it worked without hitches for me. You could try to reinstall the restricted extras package.
Didn't work.
> **Zorael said:**
> I'm not sure if it's relevant, but have you set it to be the default java engine?
Then pick OpenJava or Sun's.
I don't have OpenJava installed. It just said "nothing to configure".
> **stevoo said:**
> i may be wrong but Sun has developed a plugin that will be working with the new firefox to improve performance. That is why you do not see the java not installed. Try googling for that
I'm using Firefox 2 though.

---

### Post by ChompTheMan on 2008-05-03
Open up your file manager and go to */usr/lib/firefox/plugins/* and check if *libjavaplugin_ijo.so* is there.  If not do this:

```
cd /usr/lib/firefox/plugins/

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_ijo.so
```

Restart Firefox.  Hope this helped.

---

### Post by priegog on 2008-05-04
hmmm... I did NOT have that file in that folder, but adding it via that command didn't do the trick either. You seem to know a lot about this tho.

---

### Post by BWF89 on 2008-05-04
> **ChompTheMan said:**
> Open up your file manager and go to [

Restart Firefox.  Hope this helped.
Didn't work.

---

### Post by bjhom on 2008-05-05
I think ChompTheMan had a typo, it should have been:

```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by BWF89 on 2008-05-07
> **bjhom said:**
> I think ChompTheMan had a typo, it should have been:
I tried that out. But now the website I had that used Java isn't coming up and I don't know of any other websites that use it to test it out on.

---

### Post by priegog on 2008-05-08
I tried it too and it didn't work either. I try it out with facebook's photo upload applet.

---

### Post by jamesstansell on 2008-05-08
[http://javatester.org/version.html](http://javatester.org/version.html) is a good site to test that the java plugin is installed

---

### Post by priegog on 2008-05-08
hmmm... oddly enough that page works for me. I tried with facebook and thinkfree to make sure it wasn't a site problem. I guess both of the sites are broken then?

---

### Post by jamesstansell on 2008-05-08
> **stevoo said:**
> i may be wrong 

but Sun has developed a plugin that will be working with the new firefox to improve performance. That is why you do not see the java not installed. Try googling for that

That plugin is nice (I have it installed) but it shouldn't be necessary, and certainly isn't ready yet to recommend in general.

---

### Post by jamesstansell on 2008-05-08
> **priegog said:**
> hmmm... oddly enough that page works for me. I tried with facebook and thinkfree to make sure it wasn't a site problem. I guess both of the sites are broken then?

Well, for a liberal definition of broken, then maybe yes.  There are many possibilities for why they don't work.  A likely one is that you have openjdk-6-jre but that they require sun-java6-jre.  But I don't know that for sure.

BTW, another good tester site is browserspy

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

[http://gemal.dk/browserspy/java.html](http://gemal.dk/browserspy/java.html)

---

### Post by priegog on 2008-05-08
ok, we're getting closer I hope.
In the page you sent me I get java.VM: OpenJDK Client VM
But when I do a sudo update-alternatives --config java, the asterisk is with the sunJRE, not the open one, altho, the open one has a + sign that I cannot edit. Would that have anything to do with it?

---

### Post by jamesstansell on 2008-05-08
> **priegog said:**
> ok, we're getting closer I hope.
In the page you sent me I get java.VM: OpenJDK Client VM
But when I do a sudo update-alternatives --config java, the asterisk is with the sunJRE, not the open one, altho, the open one has a + sign that I cannot edit. Would that have anything to do with it?

There's a bug open for Firefox 2 and alternatives, that I'll look up in a minute.

I don't suppose you can switch to Firefox 3?

I've _heard_ that uninstalling all the JREs and then installing sun-java6-plugin might work, but if it's the bug I'm thinking of then I doubt it.

---

### Post by priegog on 2008-05-08
I am in FF3, should I try it? I've done the whole reinstall thing but haven't tried with removing the openJRE one.

---

### Post by jamesstansell on 2008-05-08
> **priegog said:**
> I am in FF3, should I try it? I've done the whole reinstall thing but haven't tried with removing the openJRE one.

Since you're in FF3 then you have a different problem than [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309)

Try removing the icedtea-gcjwebplugin package and running the update-alternatives for Sun's java and restarting Firefox.

If that doesn't do it try removing the openjdk-6-jre package, running the update-alternatives for Sun's java, and restarting Firefox.

---

### Post by priegog on 2008-05-08
It worked! This is what did it

> **jamesstansell said:**
> Try removing the icedtea-gcjwebplugin package and running the update-alternatives for Sun's java and restarting Firefox.


thanks a lot! Now let's if that other guy who's having problems can solve it this way.

---

### Post by jamesstansell on 2008-05-08
> **priegog said:**
> It worked! This is what did it

thanks a lot! Now let's if that other guy who's having problems can solve it this way.

Excellent!

I think he had FF2, so he should see this thread:

[http://ubuntuforums.org/showthread.php?p=4908417#post4908417](http://ubuntuforums.org/showthread.php?p=4908417#post4908417)

---

### Post by BWF89 on 2008-05-08
> **jamesstansell said:**
> [http://javatester.org/version.html](http://javatester.org/version.html) is a good site to test that the java plugin is installed
Not working :(

---

### Post by jamesstansell on 2008-05-08
> **BWF89 said:**
> Not working :(

You're on Firefox 2 instead of Firefox 3 beta, right?  If so please see the link in #24 above.

---

### Post by BWF89 on 2008-05-10
> **jamesstansell said:**
> You're on Firefox 2 instead of Firefox 3 beta, right?  If so please see the link in #24 above.
I must have passed that up, thanks.

---

### Post by jjk7288 on 2008-05-10
I had a similar problem with Java not too long ago. It wasn't in Firefox, but checking my Java at that Javatester link I find that it appears to work.

What I did to get mine functioning was to remove the package java-gcj-compat, which appears to be installed by default. Try that, see if it helps.

---

### Post by Go_Bucks on 2008-05-10
> **jamesstansell said:**
> 

Try removing the icedtea-gcjwebplugin package and running the update-alternatives for Sun's java and restarting Firefox.



That fixed my firefox 3 java problem. Thanks.

---

