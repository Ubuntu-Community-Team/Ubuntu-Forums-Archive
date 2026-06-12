---
title: "Best/Second best solution to create family cloud/backup service"
date: 2021-02-13
forum: General Help
---

### Post by forumate on 2021-02-13
Hello,

I want to run one of my computers as a family photos/videos backup server. Not only locally, but to family members that also don't live in the same house. About 10 people.

My internet connection is good and with high bandwidth and they're not going to be using it all the time so it's not a problem if they access my home network (Unless you point security issues?)

What are the steps to create shared folders on Ubuntu and let certain users access them from **different networks**? Do I need Ubuntu Server or I better just use the regular Ubuntu with GUI?
And how to secure it? Also, they will access it from Windows machines, not Ubuntu

Thanks!

---

### Post by ActionParsnip on 2021-02-13
I'd suggest SFTP. Just port forward port 22 on your router to the server. Each user can log in with a local account to the server (Use SSH keys for super security and no passwords needed (Helpful for those who can't remember passwords)) and they can mount the storage over the web and securely. If they have Windows systems then they can upload using FileZilla or even a 3rd party tool to make SSHFS mount like a network drive.
You can use Ubuntu Server or Desktop if you like for any solution you choose. The only difference is that one has a GUI by default. Nothing else is different.

---

### Post by HermanAB on 2021-02-13
+10 for a SFTP (SSH) server.  It is the easiest way to make a server that is secure.  

However, I would change the port number to something non-standard such as 2222 or whatever, to throw the script kiddies off.  On the standard port, your server will before long, get tens of thousands of login attempts per hour - change it, and it will be quiet.

If you want more fancy family features, look at Retroshare:
[http://retroshare.cc/index.html](http://retroshare.cc/index.html)

Retroshare is like your own, private, secure, Facebook+Whatsapp service.

---

### Post by dragonfly41 on 2021-02-13
There is no "best" solution. There is a balance to strike between reliability, privacy, convenience, cross-platform, cost.

My first concern is you are keeping all your eggs in one basket.
When you write "a server" or "the server" .. think of the consequences if this single point of failure is lost/crashes.

One option might be to create a [Cloudinary private account]("https://cloudinary.com/documentation/advanced_url_delivery_options") to hold your assets.
You might back them up elsewhere.

Then you might need some jquery photogallery framework to publish content on another server which draws your assets from Cloudinary.  Search "js photogallery".  There are many to choose from.

Your local server could be exposed to internet using ngrok (if your ISP allows this).
Or your local server could be your local development studio to post updates to a cloud server instance (Google, AWS, Heroku, DigitalOcean ...), which draws from Cloudinary. In a triangle: local - Cloudinary CDN - Cloud server

You might need to compose ebooks (mixed text and photos) and here you could look at many, many tools for composing stories.
Scribus, Calibre are just two. examples.
You can also use an editor such as Atom, with markdown and markdown-preview-enhanced packages .. but this is diving into development.  Nevertheless it is quite a powerful tool.

---

### Post by forumate on 2021-02-13
Thank you guys. I will setup an SSH server. But I prefer to mount as a drive on the other users Windows PC as a network drive. 
Are there tutorials on how to do both? The SSH server setup with different port, and also mount them on the Windows PCs as a network drive?

I will use RAID1 so to not lose photos in case anything happens. Also right now it's just for testing so it wont be used for sensitive data right away

---

### Post by mikewhatever on 2021-02-13
Hm..., the best... Never mind, I only know the second best.

---

### Post by forumate on 2021-02-13
> **mikewhatever said:**
> Hm..., the best... Never mind, I only know the second best.
What? That's exactly what the title says!

---

### Post by TheFu on 2021-02-13
Best is subjective.

+1 for a locked down ssh/scp/sftp/rsync server.  Many backup tools support those for cloudy backups. You mit not want to allow them ssh access, which can be disabled, while still supporting sftp.  Read up on the *chroot for sftp-server*. Different family members might want their backups protected from others having access.  Win10 supports ssh-keys just like Unix. I know it works with the cli ssh, scp, and sftp programs, but don't know about others.

Another option would be to run a nextcloud server. This can be setup to require 2FA, to prevent unauthorized access. There are official docker and lxd containers for it, so staying patched/current shouldn't be too much trouble.  This would be harder to automate the backups.

**Winscp** is a Windows scp/sftp client. Some versions of Filezilla have a bug that breaks the sftp support. Beware.

Be 100% certain that your family understands what a backup means. It s a second copy, not some magical place that will always work.  've see many people with an external drive - called "backup" - copy files over to it, then immediately delete the source files from their laptop. After all, it was safe on the "backup" drive.  ;)

Don't let your family make that common mistake.

Retroshare is pretty cool too, for what it does.

If you setup a vpn/mesh-vpn, then everyone in your family could have all the communications encrypted. Nextcloud has some great addons like a photo gallery, audio and video conference server, addressbooks, calendars, and probably 200 others. Most nextcloud addons have android apps.

---

### Post by TheFu on 2021-02-13
RAID never replaces the need for backups. Some RAID problems can only be solved by starting over and restoring backups.

---

### Post by mikewhatever on 2021-02-13
> **forumate said:**
> 

[QUOTE=mikewhatever;14020493]Hm..., the best... Never mind, I only know the second best.
What? That's exactly what the title says![/QUOTE]

I can see the original title, silly. :P

---

### Post by HermanAB on 2021-02-13
With Windows, Filezilla is by far the easiest way to access another computer over an inherently unreliable link.  

In my experience, using a network mount will be unsatisfactory, as there will be many inexplicable issues due to packet loss over the internet.

---

### Post by forumate on 2021-02-14
> **mikewhatever said:**
> I can see the original title, silly. :P
Haha oops \\:D/

> **HermanAB said:**
> With Windows, Filezilla is by far the easiest way to access another computer over an inherently unreliable link.  

In my experience, using a network mount will be unsatisfactory, as there will be many inexplicable issues due to packet loss over the internet.

Thank you. So for now it should be FileZilla! Will have to teach them how to use it haha

---

