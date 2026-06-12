---
title: "Ubuntu Installation Procedure (Wiki question)"
date: 2016-12-29
forum: General Help
---

### Post by Ifaistos on 2016-12-29
Hello everyone :-)

I understand that my question might be out of topic, but I thought that there would be others in here who have been down the same path as me, and might have some info they'd like to share.

So, the last few days I've found myself installing or re-installing or upgrading Ubuntu multiple times.
I get a weird pleasure every time I delete a windows partition to install ubuntu on a friends computer.. ( is this normal?! )

Anyway, I have my own procedure of installing and the apps that I add to each installation.
So I thought of creating a file with all the terminal commands and procedures in sequence so that I don't forget smt.
Then I would upload to my Megasync cloud storage so that I have easy access everywhere...

However if I would be installing on a friends computer it wouldn't be very practical to install any cloud storage app to have access to the file.

So I thought I would create my own online wiki, and this way I would have very easy access anywhere I am.  However I've never done this before and have 0 experience regarding wiki sites.

So the question is this :

Can someone suggest an easy (and FREE) wiki site for the purpose described above?

Thanks and Happy New Year everyone !

---

### Post by vasa1 on 2016-12-29
> **Ifaistos said:**
> ...
Then I would upload to my Megasync cloud storage so that I have easy access everywhere...

However if I would be installing on a friends computer it wouldn't be very practical to install any cloud storage app to have access to the file.
...
Why would you need to install an app? Isn't just a browser sufficient to access your cloud storage from anywhere?

---

### Post by slickymaster on 2016-12-29
> **Ifaistos said:**
> <---snip--->

So the question is this :

Can someone suggest an easy (and FREE) wiki site for the purpose described above?
<---snip--->
[DokuWiki]("https://www.dokuwiki.org/dokuwiki#")

---

### Post by howefield on 2016-12-29
+1 to using a browser to access the "cloud" storage. 

I'd probably use a USB thumb drive.

---

### Post by Geoffrey_Arndt on 2016-12-29
Yes, any browser will provide the authentication login screen unless that Cloud Server also requires local software to be installed (such as dropbox) to access the file.

The issue you will have is there is NO simple way to do what you suggest because you have to put in some time and effort into understanding the wiki technology.   In addition to understanding how to admin a wiki, the setup usually requires you to install a web-server (via LAMP or similar) and often it also requires a relational Database (mySQL, PostgresQL, etc.).   So installing LAMP (Linux Apache MySQL PHP) will solve both "initial" requirements,    Then, there is the matter of setup and admin - - - get ready for lots of reading and viewing tutorial videos on youtube.

Another option is a bit simpler (yet still powerful) wiki with available online hosting such as "TiddlyWiki" . . . . easier . . . . . but took me a few hours to understand enough how to do and to set up the online db that is offered.   Lots of reading still, but easier than LAMP.   Pretty awesome software that not enough folks are aware of.

[http://tiddlywiki.com/](http://tiddlywiki.com/)

---

### Post by vasa1 on 2016-12-29
> **Geoffrey_Arndt said:**
> Yes, any browser will provide the authentication login screen unless that Cloud Server also requires local software to be installed (such as dropbox) to access the file.
...
I feel that with clouds of the Dropbox or Google Drive type (which is all I know about), there's no need for any cloud-specific local software. All the sharer needs to do is to generate a link from within the cloud by pressing the share button.

---

### Post by Geoffrey_Arndt on 2016-12-29
Vasa, yes . . . that's right . . . I forgot about that feature.     The corporate wiki I formerly managed (Confluence) had similar capability.   I haven't needed to use sharing since retiring, but it works as you've described.   

The only distinction is when comparing a full-fledged wiki to a web app file referencing mechanism . . . the wiki has much greater capability (although more work to manage).

---

### Post by oldfred on 2016-12-30
I just have a couple of bash scripts I have on flash drive. One reconfigures system the way I want. And second installs a variety of applications. 

I did have to reconfigure my first script as I have embedded UUIDs in some of the commands. So when installing on my new system I had to update for new UUIDs.

---

### Post by Geoffrey_Arndt on 2016-12-30
Might be interesting to see the scripts and test . . . always can use new tools like that.

---

### Post by Ifaistos on 2016-12-30
Wow !

All very interesting answers!

@Vasa1 : Yes you're right.  I don't need to install local app for linux in order to access the file.  So I understand that the "wiki" solution might sound like an overkill.  To tell you the truth I was thinking of sites likes wikia.  When I said "starting my own private wiki" I though of those sites that allow you to start with just creating an account.  No need to install Lite-SQL or Apache or anything else.  Much like creating a blog with blogger or a shop with shopify (without hosting, registering a name etc..).  There are sites like that and you don't need to do any reading to get started.

Anyone has any suggestions?  (Wikia is obviously one.. I just thought that people might have used others ones with better/more/different features.

@slickymaster & @Geoffrey_Arndt  : Thank you for the suggestion.  As I said to vasa1 I only needed a much simpler solution than the one I lead everyone believe.

@oldfred : Sounds like a very interesting and much faster solution.  Could you please point me to the right direction on how to get started?  Maybe some examples?

Thanks everyone !!

---

### Post by oldfred on 2016-12-30
Most of my scripts probably will not directly help, but may give a direction.
As mentioned I have UUIDs as I directly edit fstab to add the mount of my /mnt/data partition.

It started with just a few commands that I copied from history. As I learned more ways to do things with command line more got copied from history into file. Now a lot is commented out, either obsolete at least for me, or future which I still want to confirm or do not yet use in every install.

Some clean up still required of both scripts. And they are more for me on on system, my Asus-ar for each new test install. I keep most current LTS as main working install, but install each new version a couple of times to see what has changed, but usually want config to match (and test scripts).

---

### Post by Ifaistos on 2016-12-31
Thanks for sharing !!

---

### Post by Ifaistos on 2017-01-07
So I am guessing that as far as a free wiki solution, I should go with wikia?
Anyone has used it before?  Any better suggestions?

---

### Post by slickymaster on 2017-01-09
See [post #3]("https://ubuntuforums.org/showthread.php?t=2347811&p=13588167&viewfull=1#post13588167")

---

