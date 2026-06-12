---
title: "Simple HTTP File Server like HFS on Windows"
date: 2007-02-07
forum: General Help
---

### Post by Boni2k on 2007-02-07
Hello,
I am looking for a GUI Program for Ubuntu that can easily share my files through the Internet. A very nice program for Windows was HFS (HTTP File Server). Is there something like this for Ubuntu?

Thank you, Boni

---

### Post by ^rooker on 2007-02-07
Although it's probably not what you'd consider a "nice gui", but simply install apache locally to publish your files using http.

Usually after installing apache (apt-get install apache2), you can already move some files into "/var/www/" and access them as "http://localhost/".

In case that's all you need it's set up in 5mins. If you need something else, it might be necessary to do some tweaking of Apache.

---

### Post by dannyboy79 on 2007-02-07
that will maybe allow to access your files from your own machine ([http://localhost/](http://localhost/)) but that's obviously not going to work over the internet. you need to know your ip address or get a domain name from [www.dyndns.com](www.dyndns.com) so that you don't have to type in ([http://64.54.163.15)](http://64.54.163.15)). i can only say this due to my experience when i set up proftp. when I wanted to access my server, I had to type in [ftp://64.54.163.15](ftp://64.54.163.15) for example) to see my ftp server. i wish I could help you more than this but I can only tell you that [http://localhost/](http://localhost/) won't work. I mean, think of how many other machines have this name. ha ha

---

### Post by Boni2k on 2007-02-07
I understand - Thank you!

ProFTP sounds good, I need to learn how to use this program since in a few month, I have a project from school about this - setup an ProFTPd Server.

I am trying it, I guess I can have HTTP-links for anyone, then?

Greets, Boni

---

### Post by ^rooker on 2007-02-08
http links for what?

---

### Post by etank on 2007-02-08
To add to the apache solution, once you install apache2 you can create a folder in your home dir called public_html and place the files you want to share in it. Then from a web browser go to [http://IP-Or-DNSName/~username](http://IP-Or-DNSName/~username). Make sure that the ~ is in the url.

---

### Post by m.musashi on 2007-02-08
While not a gui, webfs is a simple file share program. It's very basic and will only give access to a single folder. Of course, if that folder was /home you would have access to everything below that. However, so will the rest of the world. If you are looking for private access this is not a good choice. If you want friends and family to have access to photos or something it's a very good choice. It is in synaptic if you are interested.

---

### Post by chorca on 2007-11-04
Hey all. This was posted awhile ago, so i'm wondering if there's been any other developments since then for something like this. I use HFS extensively as well in windows to send files to friends and whatnot, it's a really nice little program to help send a file when whatever messenger is being annoying, or won't work, or you want to post a link in channel or something.

The last person here mentioned webfs, and i took a look at that, but i'm still wondering if anyone's seen any graphical utilities out there akin to HFS.

---

### Post by vikrant82 on 2008-02-29
Why dont you guys run hfs on wine.. Works like a dream ..

---

