---
title: "[SOLVED] In Firefox, cannot utilize web sites that have java redirects to https site"
date: 2008-01-07
forum: General Help
---

### Post by DugieHowsa on 2008-01-07
I am having trouble accessing the secure portions following sites:

[www.citizensbank.com](www.citizensbank.com)
[www.ticketmaster.com](www.ticketmaster.com)

I can get to the main http unsecured pages no problem.  But, when I get to a part where there is a java form that re-directs to an https page, firefox times out.  When running wireshark during the process, it appears that the action of clicking the button does nothing in the browser, as no info is ever sent to the server.

The actions in questions are pusing the "Log In" button on the Citizens Bank front page, and when clicking the "Look for Tickets" button on the ticket master page.

Java.com verification page confirms Java plugin is installed.

One unusual thing I did notice is that on the Firefox about:plugin page, there are two instances of the JRE installed.

    File name: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

    File name: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_02

Now moitce, that even though the file paths are identical, the versions are different.  Not sure how that is happening.  Perhaps that is part of the problem.

---

### Post by p_quarles on 2008-01-07
Well, I only looked at Ticketmaster, but it doesn't use Java. It uses Javascript. Do you perhaps have that disabled? Are you using NoScript?

---

### Post by DugieHowsa on 2008-01-08
You are correct.  Both sites use java script.  I was un-aware of the difference in nomenclature.

In the firefox preferences, javascript enabled box is checked.

Curious, I tested the sites on some other boxes, and they can access the secure sites with out a problem.

So I guess my question is now, where can I manipulate the javascript settings?  I am aware of the config changes that can be made on the about:config page, but is there any where else where I can modify javascript settings?

If I cannot modify these settings, is there a way to do a fresh re-install of firefox.  I already tried doing a apt-get --reinstall, but do I also need to remove my~/.mozilla directory as well?

---

### Post by p_quarles on 2008-01-08
You could try removing or renaming the .mozilla/ folder in your home directory, as its possible there's a bad setting somewhere in there. But make sure you save your bookmarks first: Booksmarks >> Organize Bookmarks >> File >> Export. 

Then, reinstall Firefox the easy way:
```
sudo dpkg-reconfigure firefox
```

---

### Post by DugieHowsa on 2008-01-08
I attempted the following steps but javascript still does not appear to work:

1)  renamed existing ~/.mozilla directory.
2) ```

sudo dpkg-reconfigure firefox

```
3)  Started firefox and unsuccessfully tested javascript.

4)  renamed existing ~/.mozilla directory.
5) ```

sudo apt-get remove firefox
sudo apt-get install firefox

```
6)    Started firefox and unsuccessfully tested javascript.

I have attached my about:config page with just the javascript entries displayed.  Can you display yours so I can compare mine with a working browser config that has javascript properly configured?

---

### Post by p_quarles on 2008-01-08
Sure thing.

---

### Post by dcstar on 2008-01-08
> **DugieHowsa said:**
> I am having trouble accessing the secure portions following sites:

[www.citizensbank.com](www.citizensbank.com)
[www.ticketmaster.com](www.ticketmaster.com)
.........

Both worked fine for me, I use the "Icedtea" Java package rather than the Sun Java.

---

### Post by DugieHowsa on 2008-01-08
It is my understanding that java and javascript are two different things.  Is it true that the javascript does not utilize the java-plugin?

---

### Post by p_quarles on 2008-01-08
> **DugieHowsa said:**
> It is my understanding that java and javascript are two different things.  Is it true that the javascript does not utilize the java-plugin?
Yep. That's correct. Java is a programming language designed by Sun Microsystems. Javascript is completely unrelated -- it's a popular implementation of Ecmascript, which is the basic standard for creating certain kinds of interactive web sites.

---

### Post by DugieHowsa on 2008-01-08
Your about:config looks pretty much the same, except for the extensions entry.  I switched my Error Console setting over to True, but still no success.

---

### Post by p_quarles on 2008-01-08
Yeah, I didn't notice anything in your about:config that would explain the problem.

Have you tried a different browser? That might help locate the problem, at least. See if those sites work for you with something else -- Opera, Epiphany, or Konqueror.

---

### Post by DugieHowsa on 2008-01-08
OK.  This is not interesting.  I installed Epiphany (sudo apt-get install epiphany-browser), Enabled javascript, and still was not able to access the sites.

---

### Post by p_quarles on 2008-01-08
> **DugieHowsa said:**
> OK.  This is not interesting.  I installed Epiphany (sudo apt-get install epiphany-browser), Enabled javascript, and still was not able to access the sites.
Yeah, I probably shouldn't have suggested Epiphany since that uses the same rendering engine as Firefox. Try Opera:
[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by DugieHowsa on 2008-01-09
Downloaded the Opera package from their web site and installed.  Checked the preferences and confirmed that javascript was enabled.

The tickmaster.com site exhibited the same behavior (not working).

BUT, when I went to the citizensbank.com site, the following javascript errors appeared in the console. {see attached}.

Unfortunately, I do not know much about javascript.  Do these errors mean anything to anyone?

---

### Post by DugieHowsa on 2008-01-09
OK.  So I got to thinking about javascript libraries.  I found a list of three javascript libraries in Gutsy:

 libkjsembed-dev libmozjs-dev libmozjs0d-dbg

So I installed them

```

sudo apt-get install libkjsembed-dev libmozjs-dev libmozjs0d-dbg

```

Still not working.  Then, I got to thinking about what the two sites have in common... javascript redirecting to https portion of the site.  But what about other javascript on the site?

It appears that when I go to [www.citizensbank.com](www.citizensbank.com), got to "Select Region" link at the top of the page, the javascript for the "Update My Region and Continue" button works!

I am at a total loss here.

---

### Post by p_quarles on 2008-01-09
I know what javascript *is*, and how to program some simple functions, but the error output is lost on me, unfortunately. 

Another thing that just occurred to: Opera has a built-in "user agent" switcher. You can try making it identify itself as Internet Explorer, as this may be an issue with the site's handling of user agent strings.

Go to the page, right-click on it with the mouse, select "edit site preferences," click on the "network" tab, and change what the browser identifies as. Any differences?

---

### Post by DugieHowsa on 2008-01-09
Well then, I'm afraid we are at an end then.  I tried the user agent in Opera and the user agent plugin for firefox with no success.

I appreciate all your help and all the cycles you spent on this issue.  I wish it could have had a more satisfying result.

---

### Post by DugieHowsa on 2008-01-11
Problem solved. I was running peergaurdnf ([http://sourceforge.net/projects/moblock-deb](http://sourceforge.net/projects/moblock-deb)). As soon as I killed that process the javascripts redirecting to https worked in all browsers. I also removed the link from the /etc/init.d directory so it will no longer start automatically on startup.

---

### Post by p_quarles on 2008-01-11
> **DugieHowsa said:**
> Problem solved. I was running peergaurdnf ([http://sourceforge.net/projects/moblock-deb](http://sourceforge.net/projects/moblock-deb)). As soon as I killed that process the javascripts redirecting to https worked in all browsers. I also removed the link from the /etc/init.d directory so it will no longer start automatically on startup.
:D 

I did something almost exactly the same a while back. I couldn't log in to any web site all of a sudden. I later discovered that I'd accidentally left the anonymization extension for Firefox on. PEBKAC strikes everyone sooner or later. 

Glad you solved it.

---

