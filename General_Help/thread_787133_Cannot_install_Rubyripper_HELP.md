---
title: "Cannot install Rubyripper HELP"
date: 2008-05-08
forum: General Help
---

### Post by McTwist724 on 2008-05-08
I've been trying for 2 days to get Rubyripper installed and I keep coming up with errors. I installed all of the dependencies I needed (at least I think) but it does not work.

cman@cman:~/Documents/rubyripper-0.5.0$ make install
`ruby configure --update-lang` #update the locale files
./rr_lib.rb:98: undefined method `bindtextdomain' for Gui_support:Class (NoMethodError)
	from configure:53:in `require'
	from configure:53:in `update_lang'
	from configure:105
	from configure:83:in `each'
	from configure:83
make: *** [all] Error 1


I used the configure command (./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr or) and I typed make install and this is what happens.

I'm so frustrated right now, I've searched all over to no avail.

---

### Post by mraudiofreak on 2008-05-23
just found this, someone posted it a few days ago

[http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper)

---

