---
title: "Questions about apt-get and Ruby / Gems / Rails installation."
date: 2007-06-04
forum: General Help
---

### Post by JeanNiBee on 2007-06-04
Hi

Here is a log of what I installed and subsequent output from a 'test'.

jbateman@the-boneyard: sudo apt-get install ruby

jbateman@the-boneyard: ruby -v
ruby 1.8.5 (2006-08-25) [i486-linux]

jbateman@the-boneyard: sudo apt-get install rubygems
jbateman@the-boneyard:gem -v
0.9.0

jbateman@the-boneyard: sudo gem install rails—include dependencies
*** This did not work. It installed as agem usually would, with no errors, but "Rails" was not in path and the files in /var/lib/gems/1.8/gems/rails-1.2.3/bin are not executable.

So I decided to do this...

jbateman@the-boneyard: sudo apt-get install rails
jbateman@the-boneyard:rails testsite
create create app/controllers 
create app/helpers 
create app/models
*** Snipped for brevity ***

jbateman@the-boneyard: cd testsite
jbateman@the-boneyard: ruby script/about

About your application’s environment
Ruby version 1.8.5 (i486-linux)
RubyGems version 0.9.0
Rails version 1.2.1
Active Record version 1.15.1
Action Pack version 1.13.1
Action Web Service version 1.2.1
Action Mailer version 1.3.1
Active Support version 1.4.0
Edge Rails revision unknown
Application root /home/jbateman/testsite
Environment development
Database adapter mysql

So it's like everything is installed properly.

But, here's the problem. Any IDE I install  that is supposed to be able to handle Ruby or Rails throw errors or tells me that no Ruby SDK is installed. No matter where I point the configuration file.  I"ve dealth with mose of this...

My actual beef and reason for this post is as follows:

Additionally a very popular Linux solution Aptana with Rad Rails for Linux claims (on the Rails side.. which bugs me the most.. that in the path /usr/bin/rails it's a SHELL Script and not the actual rails.rb file that should be there.

Can someone shed some light on this?

Thanks

---

### Post by Pragmatist on 2007-06-05
First, have you tried using Synaptic?  That might be easier.  Second, which IDE are you having a problem with? (It is easier to try and solve the problem if we focus on one of the IDEs)

---

### Post by Pragmatist on 2007-06-05
Have you seen this:

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by JeanNiBee on 2007-06-05
My understanding was that Synaptic is just a wrapper around apt-get.

I checked out that page you linked, I'll definitely try what's there.

My next question, before I do the reinstall of ruby / rails etc.. how do I 'remove / delete' what I installed with apt-get so I'm back to a clean system.

(Never was very comfortable installing software on to topd of old.. unless it's safe that is.)

Thanks.

---

### Post by Pragmatist on 2007-06-05
> **JeanNiBee said:**
> My understanding was that Synaptic is just a wrapper around apt-get... how do I 'remove / delete' what I installed with apt-get so I'm back to a clean system.


True, Synaptic is just a front-end, but it is still easier to use!  Anyway, that is a personal choice.  I use both.  

In Synaptic it is very easy to do a complete remove.  Just find the package (you can use the search feature), click the green box next to the package and select "completely remove" from the choices.

For apt, here are your resources to figure out your solution:

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=apt&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=apt&titlesearch=Titles)

This one MAY  be especially useful:
[https://wiki.ubuntu.com/AptAutoRemove?highlight=%28apt%29](https://wiki.ubuntu.com/AptAutoRemove?highlight=%28apt%29)

---

### Post by hawzor on 2007-06-12
Here is an interesting thing: I never particularly felt comfortable about Ruby Gems either, but had considered installing and eventually did install Ravencore which is done by Gems. Before you say that my anxiety below is more a Ravencore problem than a Ruby problem, observe:

My rootkithunter delivered this happy message to me...

[COLOR="Navy"]From root@[myhost] Wed Jun  6 06:27:37 2007
X-Original-To: root
From: root@[myhost](Cron Daemon)
To: root@[myhost]
Subject: Cron <root@> test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Date: Wed,  6 Jun 2007 06:27:37 -0700 (PDT)

/etc/cron.daily/chkrootkit:
The following suspicious files and directories were found:
**/usr/lib/ruby/gems/1.8/gems/actionpack-1.13.3/examples/.htaccess**

***INFECTED (PORTS:  1524 31337)***/etc/cron.daily/ravencore:
run-parts: failed to exec /etc/cron.daily/ravencore: Exec format error
run-parts: /etc/cron.daily/ravencore exited with return code 1[/COLOR]

Er, um, ***INFECTED FREAKING PORTS?!?!?!?!?!***

**[COLOR="Navy"]sudo apt-get remove ruby[/COLOR]**

followed by:

**[COLOR="navy"]rm -rf /usr/lib/ruby/[/COLOR]**

Ulcer averted. Grrrrr. :(

---

### Post by JeanNiBee on 2007-06-13
I'm shocked.

Yes I would say it's Ravencore, but the fact that you installed by gems and it could be infected is cause for concern...  you would think stuff in the gem repository would be somehow scanned or at least tested and deemed 'safe' by the maintainers.

Please keep me updated and also let me know where Ic an get that rootkit scanner to check my system. (Assuming IT isn't infected too lol)

thanks.

---

### Post by Pragmatist on 2007-06-13
> **hawzor said:**
> Before you say that my anxiety below is more a Ravencore problem than a Ruby problem, observe:

My rootkithunter delivered this happy message to me...
[COLOR=Navy]
/etc/cron.daily/chkrootkit:
The following suspicious files and directories were found:
**/usr/lib/ruby/gems/1.8/gems/actionpack-1.13.3/examples/.htaccess**

[COLOR=Black]This looks like a normal gems file to me.  Read some of the documentation and you'll see.  Don't overestimate "rootkithunter", "chkrootkit", and similar programs.  They are very far from perfect and often deliver false positives. [/COLOR]

[/COLOR]> **hawzor said:**
> [COLOR=Navy]***INFECTED (PORTS:  1524 31337)***/etc/cron.daily/ravencore:
run-parts: failed to exec /etc/cron.daily/ravencore: Exec format error
run-parts: /etc/cron.daily/ravencore exited with return code 1[/COLOR]
 
Now this definitely looks like a problem with ravencore.  Notice the run **errors**.  In the previous instance, the rootkit checker was pointing you to a file that it felt was **"suspicious"** (remember, their algorithms don't produce fine-grain results.) [/quote]

> **hawzor said:**
>  Er, um, ***INFECTED FREAKING PORTS?!?!?!?!?!***
I think it would make sense to read up on those ports and really find out the cause of the problem, rather than come and post your hysterics here.  If you actually knew the cause of the messages, then posting here, albeit without all of the huge and colored type and long strings of question-marks and exclamation points, would make sense and be helpful.

Your not installing a simple program.  Your installing a programming framework that interacts with the network, involves ports, and has security access files (like .htaccess).  I think you either read very carefully, and get help in configuriing it, or accept that everything won't instantly be setup correctly and you may get some weird messages until you sort it all out.

---

