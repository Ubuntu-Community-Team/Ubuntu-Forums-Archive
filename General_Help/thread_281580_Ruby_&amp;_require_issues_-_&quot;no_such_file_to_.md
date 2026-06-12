---
title: "Ruby &amp; require issues - &quot;no such file to load&quot;"
date: 2006-10-21
forum: General Help
---

### Post by Ashiro on 2006-10-21
I'm trying to get a simple script to work on Ruby which is incredible easy to use on Windows.  All it requires is the Mechanize library and the http-access2 lib.

I installed both using Gems but I get the following error:

> ./mir_check2.rb:1:in `require': no such file to load -- mechanize (LoadError)
        from ./mir_check2.rb:1


When I put in the direct path Ruby complains again about not being able to find the path to a require in the Mechanize library.

Its as if Ruby is looking in all the wrong places for installed libraries.  Why is this?  Can someone please help? :(

I develop in Ruby a lot so not getting any Ruby scripts to work is a pretty big downer.

---

### Post by Ashiro on 2006-10-21
This is really important to me so if anyone can help I'd be eternally grateful. :)

---

### Post by Ashiro on 2006-10-23
I've found the answer·  Just in case anyone else needs this.

Simply put this at the top of the file:

require 'rubygems'

---

### Post by Priit Tamboom on 2007-12-14
You can add:

```
export RUBYOPT=rubygems
```

to your ~/.bashrc to make ruby load rubygems always.

More info [http://rubygems.org/read/chapter/3#page70](http://rubygems.org/read/chapter/3#page70)

---

### Post by Bencornwell on 2008-04-09
Thanks guys - have just started getting into Ruby and this also had me stumped.

---

