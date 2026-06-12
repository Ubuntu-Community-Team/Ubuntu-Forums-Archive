---
title: "Instiki installation on Ubuntu"
date: 2007-08-06
forum: General Help
---

### Post by leohart on 2007-08-06
I am trying to install [Instiki]("http://instiki.org") on a Ubuntu Server installation. 

Here is what I do: I install Ruby, irb, sqlite3 and libdbdsqlite-ruby through apt-get

I installed Redcloth, bluecloth, rails via gems.

Then I download instiki (tgz package). I unpack it and rename to wiki.

Then I run ./instiki .

WEBrick starts on port 2500 and start ouputting normal access entries. 

I point my browser to localhost:2500 and was greeted with a page to create a new web. I left the default 'wiki' name and address. Then put in the password. Hit Setup.

All i see is "Unknown web wiki". This happens on 3 different Ubuntu setup. 

Am I missing something? Can someone gives me some debug information as to where to look for possible error in configuration.

---

