---
title: "[SOLVED] Fetchmail and Gmail"
date: 2008-01-22
forum: General Help
---

### Post by Levander on 2008-01-22
I've got a new Gutsy install here I'm trying to get my mail system setup.  Almost the last thing left is getting fetchmail to download my email from Gmail.

I want to do it so that fetchmail runs as a daemon, polling Gmail every so often.

I tried just copying over /etc/fetchmailrc from my old box.  I get this in syslog:

```

Jan 22 01:32:25 blink fetchmail[6276]: Server certificate verification error: unable to get local issuer certificate 
Jan 22 01:32:25 blink fetchmail[6276]: Server certificate verification error: certificate not trusted 
Jan 22 01:32:25 blink fetchmail[6276]: Server certificate verification error: unable to verify the first certificate 
Jan 22 01:32:25 blink fetchmail[6276]: sleeping at Tue 22 Jan 2008 01:32:25 AM EST for 30 seconds 

```

I looked in /usr/share/doc/fetchmail, and in the README file, it says installation and configuration instructions are included in the INSTALL file.  However, there's no file named INSTALL in that directory.

Instructions on how to proceed appreciated.

---

### Post by andrew.46 on 2008-01-22
Hi,

Your ~./fetchmailrc would perhaps look like this one:

```
poll pop.gmail.com                   # Tell fetchmail about server
with proto POP3                      # Use the POP-protocol       
user 'Gmail Username '               # Your Gmail Username            
there with password 'Gmail Password' # Your Gmail Password  
is 'username' here                   # Local Username                    
mda "/usr/bin/procmail -d %T"        # Tell fetchmail which MDA to use   
options                              # Options duh                                      
keep                                 # Keep the mail on server = safe
ssl                                  # Use ssl
sslcertck                            # Check the certificates
sslcertpath /etc/ssl/certs           # Path to the certificates
```And this supposes that you have he following installed:

```
$ sudo apt-get install openssl ca-certificates libssl0.9.8 libssl-dev
```Hopefully these settings will help you out?

             Andrew

---

### Post by Levander on 2008-01-22
Okay, thanks Andrew.  Installing the ca-certificates package did the trick.  openssl and libssl0.9.8 were already installed.  They must be installed by default.

Your instructions may be a little old, because there is no libssl-dev package anymore.  But, on my old box that I'm migrating some configuration from, libssl-dev was installed.

The documentation for fetchmail is a real mess.  I see in your configuration file above, that you're passing mail from fetchmail to an MDA.  However in the /usr/share/doc/fetchmail/README.Debian.gz file that comes with that package:

```

Fetchmail wants a MTA and will not use a MDA fallback by default anymore. 
Please configure it correctly for your system.

```

However, that README is dated 2005, so who knows if it's right or not.

Am just really surprised there aren't better instructions on how to get this up and going.  Maybe I'll look into writing a wiki page for it since I've just done it.  Even though I don't know the process inside and out.

---

### Post by andrew.46 on 2008-01-22
Hi,

 Glad it is all sorted out:

> **Levander said:**
> Am just really surprised there aren't better instructions on how to get this up and going.  Maybe I'll look into writing a wiki page for it since I've just done it.  Even though I don't know the process inside and out.

I have done a bit of work in this direction myself, and it actually was this site that I quoted to you:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

On my own personal site I have spoken of the certificates in a little more detail and shown how to manually extrace them:

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

So libssl-dev was not there? I am on my *other* partition at the moment but I shall switch over and check shortly. I suspect it will be there under a different name. Try:

```
$ apt-cache search libssl | grep dev
```and I suspect it will pop up :-)

{Edit}: Definitely there, at least in Feisty:

```
libssl-dev - SSL development libraries, header files and documentation 
```

              Andrew

---

### Post by Levander on 2008-01-22
Well, it works fine without libbssl-dev.  So, I don't think it's important if they gave it a new package name or not.  Maybe they rolled some of what was in that package into one of the other ones you listed above.

It's cool you got a web site.  But I wish you'd find a way to incorporate some of that stuff into wiki.ubuntu.com.  It's so much easier just finding stuff on the wiki than it is finding stuff spread across the internet.  Not that there's not a place for personal web sites, but instructions on how to use software seems like it should be filed with the appropriate community.

---

### Post by andrew.46 on 2008-01-22
Hi,

> **Levander said:**
> Well, it works fine without libbssl-dev.  So, I don't think it's important if they gave it a new package name or not.  Maybe they rolled some of what was in that package into one of the other ones you listed above.

The dev package should only be required for compiling. In the case of my Ubuntu page it was required to compile Fetchmail against ssl.

>  It's cool you got a web site.  But I wish you'd find a way to incorporate some of that stuff into wiki.ubuntu.com.  It's so much easier just finding stuff on the wiki than it is finding stuff spread across the internet.  Not that there's not a place for personal web sites, but instructions on how to use software seems like it should be filed with the appropriate community.Well, I am not so active in Ubuntu any more but I make an effort to look after a few 'howtos' that I have to put together. If you have a strong feeling about the Ubuntu wiki I would suggest that you should go ahead and start writing :-) Good documentation, as you have found, is hard to come by and if you see a gap you should perhaps work at filling it.

The material about certificates etc on my personal mutt page is really not suited to the Ubuntu credo and as you know the relevant certs are all supplied 'ready to go' by debian.

Good luck with the wiki!

     Andrew

---

