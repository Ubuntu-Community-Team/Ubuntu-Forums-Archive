---
title: "echo $PATH, after Ruby on Rails install"
date: 2016-06-10
forum: General Help
---

### Post by rblunt on 2016-06-10
[FONT=verdana]I've installed Rails with Postgres and RVM on a Ubuntu 16.04 virtualbox.[/FONT]
[FONT=verdana]I recorded a screenshot everytime I finished a piece of the install. I ran from the terminal "pwd" and "echo $PATH"[/FONT]
[FONT=verdana]When I finished installing and doing a new app with "rails new myapp" I was good to go.[/FONT]
[FONT=verdana]I closed and opened the terminal again, now "rails -v" and "ruby -v" don't work, neither does "rails server" obviously.[/FONT]
[FONT=verdana]Here is what I get when I run "echo $PATH"[/FONT]
[FONT=verdana]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/osboxes/.rvm/bin[/FONT]
[FONT=verdana]but this is what "echo $PATH" responded with after I did the install of rails[/FONT]
[FONT=verdana][http://imgur.com/u3szwEP](http://imgur.com/u3szwEP)[/FONT]
[FONT=verdana]What have I done wrong? or not done?[/FONT]
[FONT=verdana]I used this tutorial, went for the RVM option and Postegres to set it up. I've done this multiple times, same result, that is why this last time I kept track of it with "pwd" and "echo $PATH" I am not an Ubuntu expert. I thought thought I should work with Rails the way a professional would, and it gave me some experience with setting up a virtualbox VM that isn't Windows.[/FONT]
[FONT=verdana][https://gorails.com/setup/ubuntu/16.04](https://gorails.com/setup/ubuntu/16.04)[/FONT]

---

