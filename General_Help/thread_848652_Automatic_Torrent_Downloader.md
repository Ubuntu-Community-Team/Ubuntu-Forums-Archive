---
title: "Automatic Torrent Downloader?"
date: 2008-07-03
forum: General Help
---

### Post by mtgmutton on 2008-07-03
I have been searching around, and I just can't seem to find a program (or a Deluge plugin) for Linux Mint (based off of ubuntu) that will automatically download a torrent for me without an RSS feed. Does anyone know of a program that will download a torrent when it is added to a page? Or, if not, how to make one? Any help would be greatly appreciated!

---

### Post by kamitsukai on 2008-07-03
[FONT="Comic Sans MS"][SIZE="2"]> **mtgmutton said:**
> I have been searching around, and I just can't seem to find a program (or a Deluge plugin) for Linux Mint (based off of ubuntu) that will automatically download a torrent for me without an RSS feed. Does anyone know of a program that will download a torrent when it is added to a page? Or, if not, how to make one? Any help would be greatly appreciated!

I'm also interested if something like this exists!:lolflag:[/SIZE][/FONT]

---

### Post by milosz.galazka on 2008-07-03
The easiest way to do this is to use python/ruby/... to read and parse page so it could download new torrents.

There are many tools that will help you like [http://code.whytheluckystiff.net/hpricot/](http://code.whytheluckystiff.net/hpricot/)

---

### Post by mtgmutton on 2008-07-03
"sudo gem install hpricot --source [http://code.whytheluckystiff.net](http://code.whytheluckystiff.net)
Bulk updating Gem source index for: [http://code.whytheluckystiff.net](http://code.whytheluckystiff.net)
Select which gem to install for your platform (i486-linux)
 1. hpricot 0.6 (ruby)
 2. hpricot 0.6 (mswin32)
 3. hpricot 0.6 (jruby)
 4. hpricot 0.5.150 (jruby)
 5. hpricot 0.5.150 (ruby)
 6. hpricot 0.5.150 (mswin32)
 7. Skip this gem
 8. Cancel installation
> 1
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install hpricot --source [http://code.whytheluckystiff.net](http://code.whytheluckystiff.net)
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:1


Gem files will remain installed in /var/lib/gems/1.8/gems/hpricot-0.6 for inspection.
Results logged to /var/lib/gems/1.8/gems/hpricot-0.6/ext/hpricot_scan/gem_make.out"



....what? could you please explain to me what just happened? I installed ruby, but I have no clue what to do to fix this...

---

### Post by milosz.galazka on 2008-07-03
Similar problem was [here]("http://ubuntuforums.org/showthread.php?t=592563")

---

### Post by mtgmutton on 2008-07-03
yet when I choose "3. hpricot 0.6 (jruby)", this is what i get

"sudo gem install hpricot --source [http://code.whytheluckystiff.net](http://code.whytheluckystiff.net)
Select which gem to install for your platform (i486-linux)
 1. hpricot 0.6 (ruby)
 2. hpricot 0.6 (mswin32)
 3. hpricot 0.6 (jruby)
 4. hpricot 0.5.150 (jruby)
 5. hpricot 0.5.150 (ruby)
 6. hpricot 0.5.150 (mswin32)
 7. Skip this gem
 8. Cancel installation
> 3
Successfully installed hpricot-0.6-jruby
Installing ri documentation for hpricot-0.6-jruby...
Installing RDoc documentation for hpricot-0.6-jruby..."

Now that's done :)

---

### Post by mtgmutton on 2008-07-03
I'm sorry, but I'm not so good with code :(  I'm not sure what all this stuff on the "basics" page means... When I put the first command in, it says "bash: require: command not found". Where should I be putting this in? Is this a CLI program?

---

### Post by mtgmutton on 2008-07-03
I tried putting "require 'rubygems'" and "require 'hpricot'" into python instead but all I got was:

require 'rubygems'
  File "<stdin>", line 1
    require 'rubygems'
                     ^
SyntaxError: invalid syntax

so I entered:

 help(require)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'require' is not defined

Now I'm totally lost... Am I supposed to know Python for this? I don't know much. at least not enough to get this done apparently... :(

---

### Post by milosz.galazka on 2008-07-04
Can you put here that page address?

---

### Post by mtgmutton on 2008-07-05
[http://code.whytheluckystiff.net/hpricot/wiki/HpricotBasics](http://code.whytheluckystiff.net/hpricot/wiki/HpricotBasics)

Hpricot basics. BTW i'm reading a book... python for dummies :)  I'm learning quite a bit, but i haven't gotten to the HTML section yet... I'll have finished the book by the end of the weekend... Maybe then I'll know what I'm doing  :)

---

### Post by mtgmutton on 2008-07-06
I didn't finish the book, but I know more now. I wrote my own program for this, and it gets the links well, but I can't get it to open the .torrent file link. Does anyone know how to make it do this? This is what I have for a program so far:

import urllib
import urllib2
import htmllib, formatter
from cStringIO import StringIO

dattebayo = urllib2.urlopen('http://dattebayo.com/t/')
html = dattebayo.read()
dum = formatter.DumbWriter(StringIO())
fourmat = formatter.AbstractFormatter(dum)
parsley = htmllib.HTMLParser(fourmat)
parsley.feed(html)
parsley.close()
dattebayo.close()

I'm not sure where to go next. Whenever I type in "find(insertlinkhere)", it gives me a syntax error. Does the find part have to be in the program?

---

### Post by mtgmutton on 2008-07-06
I decided to change it up...

import urllib

f = urllib.urlopen("url")
g = f.read()
file = open("filename", "w")
file.write(g)
file.close()

This works, but I want to make it keep running and put the file into Deluge so I don't have to... Any ideas?

---

### Post by mtgmutton on 2008-07-06
I think this could be my final code for now... It should work in an endless loop until the file shows up on the server. Then it downloads it to a user-specified directory, which I set Deluge to autoload from. It's always good to have some peer-to-peer criticism...


import urllib

f = urllib.urlopen("FileURL")
while "SameFileURL" is 'false':
[indent]f()[/indent]

g = f.read()
file = open("PlaceIWantToSaveItTo", "w")
file.write(g)
file.close()

Any comments would be helpful!

---

