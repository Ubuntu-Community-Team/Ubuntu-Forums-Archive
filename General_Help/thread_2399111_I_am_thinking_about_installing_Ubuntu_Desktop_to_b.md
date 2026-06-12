---
title: "I am thinking about installing Ubuntu Desktop to be used as a simple webserver. Ok?"
date: 2018-08-21
forum: General Help
---

### Post by petenoob on 2018-08-21
From what I can gather, since they have the same kernel and the same distribution, the Ubuntu desktop 18.04 and Ubuntu Server 18.04 are exactly the same if I strip the desktop of it's GUI and other things, is that correct?

So there will no performance issues between both if I do this?

Some background, I will be dual booting Wins 10 and Ubuntu Desktop. Windows for play and Ubuntu for work. The Ubunut will run a simple web browser, with around 40 tablets communicating with it concurrently, and no heavy up and down traffic, just simple fetch and feedback (moodle questions). And from people that I have talked to 40 users connecting concurrently is nothing for a web server. 

And you may ask why not install Ubuntu Server instead of Desktop. Because I can't get Server to dual boot properly but I can with Desktop! Gotten to be annoying to fix the grub so I just gave up!

Thanks for you time.

EDIT: The webserver will be used as a intranet so it will not be used 24/7

---

### Post by QIII on 2018-08-21
Hello!

Just install the server version.  Don't dual boot or when you shut off Ubuntu to boot windows, you'll kill the server.  Install your server in a virtual machine instead.  I have about a dozen VM servers running on my home network at any given time.

The server version comes with what you will need.  The desktop version doesn't come with some of the server-specific packages by default.

Best to start off learning the "right way" to do a Linux web server.  Even stripped of the GUI, the desktop version will probably leave some services running that you don't need or want.  With a web server, you want the barest minimum of services running.  

Every running service is an attack vector.  Only run what is absolutely necessary.

Cheers!

---

### Post by petenoob on 2018-08-21
Hi Quill, my mistake, I'm going to run the webserver like an intranet, and will use it adhoc, when I need to , so shutting it down is fine. I've edited my OP.

With much humilty as possible, and not trying to sound aburpt, I want to learn linux properly but that's secondary for me, I just want to get the moodle server running, as filling in content is time consuming, and much more interesting. It's been a week of trying to get the dual boot running both OS but keep opening cans of worms everywhere.

So my original question still stands. A stripped down desktop is pretty much the same performance as the server version. 

I'm dual booting because it's easier for me to play in Windows, sad to say, but I'm reliant on it for the moment.

---

### Post by HermanAB on 2018-08-22
While you are learning, using a desktop machine is good.  Once you got the basics figured out, install KVM and make a VM with a server in that.

If you are running Win10, then you could install Virtualbox from the Oracle web site and experiment in that.  The Win10 scheduler is almost as good as a Macintosh so it will work quite well.

---

