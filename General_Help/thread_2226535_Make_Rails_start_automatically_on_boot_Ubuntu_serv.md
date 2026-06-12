---
title: "Make Rails start automatically on boot Ubuntu server 14.04"
date: 2014-05-27
forum: General Help
---

### Post by Nathan_Berg on 2014-05-27
Hello all, I am building a Rails server on Ubuntu server 14.04 and have got it all up and running. I haven't been dealing with Linux or Rails for all that long so apologies in advance for any ignorance that I have. Also, apologies in advance if I have put this post in the wrong section.

Anyways, I would like to make it so that my rails server will automatically start whenever the machine is rebooted since it is kind of a pain to have to "cd /mywebapp && rails server" manually every-time that that I want to start rails up again. I have created a script that looks something like:

#!/bin/bash
cd /my/web/app/
rails s

I then added the scripts full path the my rc.local file with the hopes that it would then start automatically. I've had no luck with that.

I have also added the script to my init.d folder and ran the sudo update -rc.d rails defaults command. However when it still does not run at bootup and upon running service rails start, I only get ruby errors.

I have made the observation that if I run my rails startup script as "sudo" (sudo ./rails) then I end up getting a man page for rails, whereas if I do not run the script as sudo (./rails) the script works perfectly. Perhaps this is why the rc.local is failing to run the script?

Anyways, any pointers to steer me in the right direction would be highly appreciated.

---

### Post by tgalati4 on 2014-05-27
If rails is an upstart service then you should be able to:

```
sudo service rails start
```

My rails apps are bundled in a few bitnami stacks, and they work out-of-the-box, so I never paid attention in rails class.

---

### Post by Nathan_Berg on 2014-05-28
By the way, this is the first init.d script I've attempted to create... so I wouldn't doubt that I am doing it totally wrong XD

Anyways, I was thinking that I'd be able to run the script with sudo service rails start as well... I can run the script with ./rails (since that's the name of my init.d script) and it works perfectly.

My init.d script looks like:
#!/bin/bash
cd /home/myusername/myapp
rails server

But when I try using service rails start I get a bunch of ruby errors:

[FONT=Menlo]/home/nathan/.rvm/rubies/ruby-2.1.2/lib/ruby/2.1.0/rubygems/dependency.rb:298:in `to_specs': Could not find 'railties' (>= 0) among 14 total gem(s) (Gem::LoadError)[/FONT]
[FONT=Menlo]        from /home/nathan/.rvm/rubies/ruby-2.1.2/lib/ruby/2.1.0/rubygems/dependency.rb:309:in `to_spec'[/FONT]
[FONT=Menlo]        from /home/nathan/.rvm/rubies/ruby-2.1.2/lib/ruby/2.1.0/rubygems/core_ext/kernel_gem.rb:53:in `gem'[/FONT]
[FONT=Menlo]        from /home/nathan/.rvm/gems/ruby-2.1.2/bin/rails:22:in `<main>'[/FONT]
[FONT=Menlo]        from /home/nathan/.rvm/gems/ruby-2.1.2/bin/ruby_executable_hooks:15:in `eval'[/FONT]
[FONT=Menlo]        from /home/nathan/.rvm/gems/ruby-2.1.2/bin/ruby_executable_hooks:15:in `<main>'


[/FONT]

---

### Post by btindie on 2014-05-28
That's not an init.d script you've written, just a general bash script. Take a look at /etc/init.d/skeleton for an example, and the others in that directory.

It might help if you looked into how the init.d scripts worked which would give you a better understanding of what's going on. [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto) [http://www.cyberciti.biz/tips/linux-write-sys-v-init-script-to-start-stop-service.html](http://www.cyberciti.biz/tips/linux-write-sys-v-init-script-to-start-stop-service.html)

Presumably your rails app needs to run under your user account? When the init scripts are run they're called as root so that'll be all wrong. You'd probably need to use su to switch user when you start your rails server.

Why don't you just run it under apache+passenger or nginx+unicorn?

Update: Google 'rails server init.d' and it throws up the following
[http://blog.sam-pointer.com/2011/03/24/starting-a-rails-instance-automatically-on-boot-on-ubuntu-server.html](http://blog.sam-pointer.com/2011/03/24/starting-a-rails-instance-automatically-on-boot-on-ubuntu-server.html)

---

### Post by Nathan_Berg on 2014-05-29
Thank you for the response :)
Apologies for my ignorance, good information for me to know in the future when trying to make init.d scripts.

I came across that page as well. However, upon following that tutorial I yielded no success.
I changed the variables in that script to the following:
[FONT=Menlo]PATH=/sbin:/usr/sbin:/bin:/usr/bin[/FONT]
[FONT=Menlo]USER=**"nathan"**[/FONT]
[FONT=Menlo]PORT=3000[/FONT]
[FONT=Menlo]RAILS_ROOT=**"/home/nathan/myapp/"**[/FONT]
[FONT=Menlo]COMMAND=**"ruby script/server -e production -p $PORT -d"**[/FONT]
[FONT=Menlo]DESCRIPTION=[/FONT][B]"Rails instance"
[/B]
When I run "service rails start", it asks for my password (good start), but after this. It just ends up saying "bash: ruby: command not found"

I also tried:

[FONT=Menlo]PATH=/sbin:/usr/sbin:/bin:/usr/bin[/FONT]
[FONT=Menlo]USER=**"nathan"**[/FONT]
[FONT=Menlo]PORT=3000[/FONT]
[FONT=Menlo]RAILS_ROOT=**"/home/nathan/myapp/"**[/FONT]
[FONT=Menlo]COMMAND=**"rails server"**[/FONT]
[FONT=Menlo]DESCRIPTION=[/FONT][B]"Rails instance"


[/B]When I run service rails start with this script, I get an output of "bash: rails: command not found"

I'm not running under a different server since I'm not really "deploying" my web app. It's still in development, but it's just a burden to have to start rails manually all the time :/

---

### Post by Nathan_Berg on 2014-06-13
I have found the solution to this. It had to do with me using RVM. I had to create a "wrapper" script and then create an init.d script that referenced the wrapper script.

---

### Post by askar2 on 2014-07-22
> **Nathan_Berg said:**
> I have found the solution to this. It had to do with me using RVM. I had to create a "wrapper" script and then create an init.d script that referenced the wrapper script.

Hi! Can you please write here your solution? Thanks in advance.

---

