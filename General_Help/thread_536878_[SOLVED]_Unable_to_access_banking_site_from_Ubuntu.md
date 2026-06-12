---
title: "[SOLVED] Unable to access banking site from Ubuntu"
date: 2007-08-28
forum: General Help
---

### Post by viking777 on 2007-08-28
I have an internet banking account with HSBC and I am not able to access it from Ubuntu. I have tried both Firefox and Konqueror but neither work. If I boot into windows then either Firefox or Internet Explorer will load the site without bother. When I use Windows to access it, after the initial screen in which you enter a username, another screen is loaded in which you enter a date of birth and characters from your password. In Ubuntu this second screen never appears, instead it jumps straight to another page telling me that I have entered incorrect data and should try again. Since I never had the opportunity to enter any data in the first place, this message is not surprising. 

I have both Java and Javascript enabled, and although I have popup windows blocked, I have set an exception for the hsbc site to allow these, but still it doesn't load that second page.

Does anyone have a fix for this?

---

### Post by bigken on 2007-08-28
I have no problems with hsbc on line what does it say ie error report

---

### Post by bigken on 2007-08-28
try it with the pop ups enabled

---

### Post by sonofusion82 on 2007-08-28
about 1.5 years ago, HSBC Malaysia's website totally prevents any other browsers from using except IE from even going to login page. I wrote an email to them complaining that Firefox is a growing web browser that they should not ignore and blah blah blah... then I got a reply saying they will look into that.
A few months later, they revamped the site and it works fine with Firefox and Konqueror. So, yup, I'm pretty happy with their customer services and stuff except their service charges and fees are little more expensive compared to the local banks.

---

### Post by PmDematagoda on 2007-08-28
I just tried to login into HSBC Sri Lanka and i got a notice that only IE and Netscape is supported, really a bank like HSBC should know better than not to support a web browser like Firefox! I'm going to have to complain.

By the way how do you lodge a complaint?

---

### Post by viking777 on 2007-08-28
Thanks for replies. I already tried it with popups enabled and it didn't work. Also, as I said, I have an exception set for this site to allow popups anyway. As for error messages, it is simply as I said before, it pops up a page saying my login information is incorrect when I haven't even had the chance to enter any. As for HSBC not allowing Firefox then that is not the case here in the UK as it will accept Firefox as long as it is from Windows.
Also I didn't say this on the original post, but I have also installed the 'User Agent Switcher' add-on for Firefox that can supposedly spoof a Windows/IE or Opera or Netscape login. I have tried all three options on this site and none of them allow me to log in.

---

### Post by Steve1961 on 2007-08-28
Try installing the [user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") and then pretend your running IE6

---

### Post by PmDematagoda on 2007-08-28
Thanks, the User Agent Switcher works perfectly.:) I found the way to complain but I don't think a 16 yr old can lodge a complain cause they ask your name.:(

---

### Post by viking777 on 2007-08-29
Don't know if it will help anyone to diagnose this problem, but the page that does not appear when using Linux is a Javascript page. Probably not much help but you never know.

BTW I use a couple of other internet banking sites as well as the HSBC one and they all work perfectly in Ubuntu, this is the only one that wont.

Another point to remember is that I have exactly the same problem if I try to use Konqueror, so this is almost certainly not a Firefox problem.

The problem is exactly the same in PCLinux btw neither Konqueror nor Firefox will work with this site. One thing I did notice on PCLinux though is that Konqueror issued a warning about blocked popup windows (this didn't happen in Ubuntu). Unfortunately it advised that in order to allow the popup I had to click a certain icon in the status bar. Unfortunately that icon does not exist.

---

### Post by viking777 on 2007-08-29
I just tried it from a Puppy Linux cd and that loads it without problem (it uses seamonkey web browser).

---

### Post by viking777 on 2007-08-29
And I just tried installing Galeon and Iceape and neither of those could load it either.

---

### Post by bigken on 2007-08-29
well I dont understand it at all I have being using ubuntu for two years and never had any problems with hsbc using firefox/swiftfox

---

### Post by viking777 on 2007-08-29
> **bigken said:**
> well I dont understand it at all 

You and me both bigken. 

Incidentally, since Seamonkey worked on Puppy I thought I would try that as well. I couldn't find it on the Ubuntu servers but I did find it on the PCLinux ones. I installed on PCLos and the result was exactly the same - it just missed out the login page where you enter your details and went straight to the 'login failed' page:confused:

It has to be something specific to my machine I think which is why it works when you access it from a live cd such as Puppy but not when anything is installed, but don't ask me what it is. I am running Gutsy which of course is still officially in development and it is a 64 bit machine which sometimes presents difficulties as I found out earlier today when I wanted to load a site that uses 'Flash' animations. That was easy to solve, but this most definitely isn't. 

Thanks for thinking about it anyway. If you come up with any ideas please let me know.

---

### Post by viking777 on 2007-11-17
I thought I would go back to this old thread to say that it is now solved for me. Trouble is I can't tell you why. Maybe something has changed in Firefox/Gutsy that has made the difference or maybe HSBC have changed something in their website that now makes it work. In any event it does work and it wasn't as a result of anything that I did!

---

### Post by DugieHowsa on 2007-12-07
I'm not sure if anyone is still monitoring this thread, but I am having a similar problem with the Citizens Bank on-line bank site.  It appears to be having a problem with the javascript:doLoginLocal('login') that is executed when you click on the login button.  I believe that I have the JRE installed correctly as:

1)  The verification page at [http://www.java.com](http://www.java.com) says that I do
2)  The about:plug-ins command issues from my web browser says I do.

I tried installing the User Agent Switcher an setting it as IE7 - Vista, but I am still not successful.  Does anyone have any other thoughts?

---

### Post by DugieHowsa on 2007-12-15
Finally... it looks like everything is now working.

First, I went to the about:config page in firefox and set the following value to true:

plugin.expose_full_path

Next, I went back to the about:plugins page in firefox.

Upon further review, I found that I had 2 instances of java plugins, both trying to execute from different directories.

The official Ubuntu sun-java6 binaries are installed in /usr/lib/jvm . I deleted the other java directory from my machine.

I then confirmed that all the java plugin links were pointing to the remaining java plugin binary.  This included the following:

```

/usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/usr/lib/firefox/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Finally, I restarted firefox, and went back to the about:plugins page to confirm there was only one instance of the java plugin installed.  Upon revisting the Java test pages, the java plugin was recognized successfully.

---

