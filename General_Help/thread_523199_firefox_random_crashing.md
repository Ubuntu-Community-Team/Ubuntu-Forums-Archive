---
title: "firefox random crashing"
date: 2007-08-11
forum: General Help
---

### Post by HarmonicaGoldfish on 2007-08-11
Today my firefox browser is crashing like nuts. There doesn't seem to be any rhyme or reason to it. I could be in the middle of typing or browsing sites and it just shuts down with no warning. It has happened about 5 times so far today. Compared to hardly ever in the past.

I run 7.04, using firefox. I copied this from the firefox about splash on my computer:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061208 Firefox/2.0.0.1

Anyone else having this problem?

thanks!

---

### Post by kellemes on 2007-08-11
Yes.. I do..
I haven't pinpointed it yet I'm afraid.
As an alternative you may look at Opera, I use this besides Firefox.

---

### Post by bollix47 on 2007-08-11
> **HarmonicaGoldfish said:**
> Today my firefox browser is crashing like nuts. There doesn't seem to be any rhyme or reason to it. I could be in the middle of typing or browsing sites and it just shuts down with no warning. It has happened about 5 times so far today. Compared to hardly ever in the past.

I run 7.04, using firefox. I copied this from the firefox about splash on my computer:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061208 Firefox/2.0.0.1

Anyone else having this problem?

thanks!

Have you tried doing an update thru synaptic?  Your version of Firefox is 5 versions old.  Current is 2.0.0.6.

---

### Post by HarmonicaGoldfish on 2007-08-12
thanks - I'll try that. 

Just out of curiosity - why is it so old? I generally receive automatic updates so never thought to have to do it manually...

---

### Post by HarmonicaGoldfish on 2007-08-12
ok - so I just checked synaptic and v. 2.0.0.6 had already been installed. So I did a reinstall. When I click the icon to start it up (and I tried both my shortcut and from the menu) it opens up the same old 2.0.0.1.

Why?

Is there something I need to do to change the version of firefox that opens from the menu to the latest install?

---

### Post by bollix47 on 2007-08-12
Have you ever done a manual install of Firefox?

Check the properties for your Firefox startup icon.  Is it pointing to /usr/lib/firefox/firefox-bin?

Use the locate command in a terminal to see if you have multiple firefox-bin files.

```
locate firefox-bin
```

Here's my build ID:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty) - Build ID: 2007073113

Mine is 64-bit but other than that your ID should be similar.

---

### Post by Paso on 2007-08-12
Mine too is crashing continuously...  it's a miracle I could read this thread till the end!

Crashes also in safe mode; already uninstalled every plugin and theme. Uninstalled also java and flash. Removed also my .mozilla profile and recreated. Cleared caches. 
Reinstalled with synaptic.... sigh... keeps crashing randomly!

version is the same, the latest:
 Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

host is Ubuntu 7.04 almost "plain vanilla", installed three days ago, updated fully.

HELP!

---

### Post by Old Pink on 2007-08-12
Seriously? That's pretty weird. No problem here.

Just a suggestion, try installing the non-ubuntu version yourself from firefox.com:

[http://download.mozilla.org/?lang=en-GB&product=firefox-2.0.0.6&os=linux](http://download.mozilla.org/?lang=en-GB&product=firefox-2.0.0.6&os=linux)

Or try Firefox 3 (Now in Alpha 7) which is very stable and saves RAM usage, I've tried [Alpha 6](http://www.mbhoy.com/05-07-2007/gran-paradiso-alpha-6) myself, which is brilliant.

---

### Post by HarmonicaGoldfish on 2007-08-12
bollix47 - when I check the properties it points to this:

firefox %u

When I typed in 'locate firefox-bin' I got this as an answer:

harmonicagoldfish@harmonicagoldfish:~$ locate firefox-bin
/opt/firefox/firefox-bin
/opt/swiftfox/firefox-bin
/usr/lib/firefox/firefox-bin
/usr/lib/swiftfox/firefox-bin
harmonicagoldfish@harmonicagoldfish:~$ 

So how do I proceed?
:)

---

### Post by bollix47 on 2007-08-12
Somehow you've managed to get 4 versions of Firefox on your system.  Did you use  automatix or some other system to add Swiftfox?  If so, you can probably use it to uninstall.

When you open Firefox can you "check for updates" under help?  You might need to start it with sudo using alt-f2 or terminal.

```
sudo firefox
```

Try running the following in a terminal and see what version you get:

```

/usr/lib/firefox/firefox-bin
```


Also, with Firefox closed, check under System>Preferences>Preferred Applications to see if there is more than one choice for Firefox.  You may be able to change the one that's starting up this way.

---

### Post by HarmonicaGoldfish on 2007-08-12
Thanks - I did the update through terminal, it wouldn't let me check for updates until I did that.
And it worked :)

my build ID is now
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6

though, this came up in the terminal after I typed in my password. Don't know what it all means.

> (Gecko:5644): libgnomevfs-WARNING **: Could not create per-user Gnome application-registry directory: /root/.gnome/application-info

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

(Gecko:5644): libgnomevfs-WARNING **: Cannot open '/root/.gnome/application-info/user.applications' for writing



When I ran '/usr/lib/firefox/firefox-bin' in the terminal I got this

> 
harmonicagoldfish@harmonicagoldfish:~$ /usr/lib/firefox/firefox-bin
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
harmonicagoldfish@harmonicagoldfish:~$ 

When I checked my preferred applications the web browser menu indicated custom with this command
> /opt/firefox/firefox "%s"

When I open the menu I have a choice between custom, epiphany, firefox, and ubuntu sensible browser.

interestingly I recently installed swiftweasel and it is not an option (though it is in my applications menu) (unless that is the 'ubuntu sensible browser')

---

### Post by bollix47 on 2007-08-12
It appears you're using the Mozilla version of Firefox rather than the Ubuntu version.

Sorry about the wrong info re starting the Ubuntu version.

Should have been:

```
/usr/lib/firefox/firefox
```

---

### Post by HarmonicaGoldfish on 2007-08-12
is that a problem? Should I try to change things?

Though I don't know exactly how I'd do that... :)

When I give the command

/usr/lib/firefox/firefox

it opens mozilla firefox, but nothing happens in the terminal. 

It appears to be the same version that opens when I use the icon on my panel.

---

### Post by bollix47 on 2007-08-12
It's not a serious problem but you will have to remember the method you used to update it as updating thru synaptic will only update the Ubuntu version.

Also, you may have problems with certain plugins that you install via synaptic as they will install for the Ubuntu version but not the Mozilla one.

Compare the following two folders and you should see a difference:

/usr/lib/firefox/plugins

/opt/firefox/plugins

If you used automatix or some other script to install the Mozilla version then that script may also have a way of installing the plugins or linking them to the /usr/lib/firefox/plugins.

---

### Post by HarmonicaGoldfish on 2007-08-12
I used automatix way back when I had dapper but not since then. 

I just tried to open the version of automatix i have to see if i could uninstall but I got the message

this version of automatix is for 6.06 only 

and I can not open it. 

So I basically do not know how my most recent version (before today's upgrade to 2.0.0.6) firefox installed because it has certainly changed since dapper drake!

Anything else I can do?
I think I would rather run the ubuntu version so I get the correct updates on time...

---

### Post by HarmonicaGoldfish on 2007-08-12
both folders are identical

---

### Post by bollix47 on 2007-08-12
If you want to use the Ubuntu version then right click on your icon for Firefox and select properties.  In the command line change from 

firefox %u 

to

/usr/lib/firefox/firefox %u

The %u isn't really necessary.

Also, try System>Preferences>Preferred Applications and change the browser entry from custom to Firefox.

The Mozilla Firefox quite possibly goes back to the install thru Automatix if you just did a dist-upgrade instead of a clean install.  If you want to uninstall Automatix check for it in Synaptic or add/remove programs.  Not really sure if it added itself back then.  Or, just leave it until your next upgrade and maybe do a clean install if you can.  Having your /home on a separate partition makes a clean install fairly straight-forward but if it's not then you would have to backup or lose it.

---

### Post by HarmonicaGoldfish on 2007-08-12
Thanks for all your help - I really appreciate it!

---

