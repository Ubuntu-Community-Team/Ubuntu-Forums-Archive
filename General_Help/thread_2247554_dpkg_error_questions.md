---
title: "dpkg error questions"
date: 2014-10-08
forum: General Help
---

### Post by volkerbradley on 2014-10-08
I deleted and reinstalled the 64-bit plex media server
The server seems to function well but I continue to see:
Errors were encountered while processing:
plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I run sudo apt-get -f install I see:
dpkg: error processing package plexmediaserver (--configure):
subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

Where would I find what the dpkg error code (1) is during this installation?
Also, where would I find what the post installation script error exit status 2 is?
Thanks.

---

### Post by ian-weisser on 2014-10-08
> **volkerbradley said:**
> Errors were encountered while processing:
plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)

dpkg error code 1 merely signals failure. In shell scripts, error code 1 usually means general (unspecified) failure.
It simply means that the install of plexmediaserver was not successful.
It's up to the user to read the error messages that explain the myriad of possible causes.

> **volkerbradley said:**
> dpkg: error processing package plexmediaserver (--configure):
subprocess installed post-installation script returned error exit status 2

Now that's more useful.
The 'plexmediaserver' package includes a post-installation script.
That script is failing.
You would need to examine that shell script to determine why it's throwing error code 2. In shell scripts, error code 2 usually means a script error (bad keyword, missing command, empty function, etc.)
If the problem is obvious, you can fix it or workaround it - it is just a shell script, after all.
Do remember to file a bug report if you think the problem is likely to affect other users.

---

### Post by volkerbradley on 2014-10-09
Thanks for responding.
You stated: "You would need to examine that shell script to determine why it's throwing error code 2. In shell scripts, error code 2 usually means a script error (bad keyword, missing command, empty function, etc.)"
Where would I find that shell script?  
Also, is there a way to enable a log file somewhere to determine what is happening? 
It may seem that I have not read anything about dpkg but have actually spent three days reading all sorts of dpkg documentation, have read the /var/log/dpkg.log, did dpkg -L plexmediaserver, etc.. 
In spite of all of my reading I am unable to understand where the error is.

---

### Post by ian-weisser on 2014-10-09
> **volkerbradley said:**
> Where would I find that shell script?  
It's compressed inside the package.
The package is located in /var/cache/apt/archives . You can examine the contents it using the normal file manager and file roller.

> **volkerbradley said:**
> Also, is there a way to enable a log file somewhere to determine what is happening?
Perhaps.
Though it probably wouldn't be much more useful than what you already know: The post-install script is broken somehow. You won't know how until you see what it's trying to do.


> **volkerbradley said:**
> In spite of all of my reading I am unable to understand where the error is.
It's not a dpkg error. Dpkg is merely passing along the error messages (and then wrapping them in it's own error message).
It's a broken post-install script.
Since I don't have that package installed, I can't see that post-install script.

If it were an official Ubuntu package, I could look up the post-install script on launchpad.net.
But 'plexmediaserver' doesn't seem to be an Ubuntu package. Where did you get it from? Website? PPA?

---

### Post by volkerbradley on 2014-10-09
I downloaded the .deb file from [https://plex.tv/downloads](https://plex.tv/downloads) - the official Website for plexmediaserver.
Thanks

---

