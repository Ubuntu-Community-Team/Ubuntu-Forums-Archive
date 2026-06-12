---
title: "RubyForge and devel of Alexandria Book Collection Mamager?"
date: 2007-02-13
forum: General Help
---

### Post by chaplanger on 2007-02-13
I am running Ubuntu 6.10 -- recently RubyForge's application '' Alexandria Book Collection Manager" crashed and will not restart.  Uninstalling and reinstalling are all to no avail.  I placed a support request at RubyForge, but it continues to go unassigned. . .  latest update of this program was Oct 7, 2005.

Though dormant since 2005, RubyForge is looking for those who would like to help in development.  If I knew anything about code, I would be there.   Here's a selfish plug to join the development team at Ruby Forge if you are skilled in code .  See what they are looking to do ([http://rubyforge.org/forum/forum.php?forum_id=11581](http://rubyforge.org/forum/forum.php?forum_id=11581))

My program's non-usability issue is a priority 3 for RubyForge at this time and remains unassigned.

Looking for help either for my issue or for RubyForge development team:

Here's the output from the terminal when I attempt to start the program:

> david@david-desktop:~$ /usr/bin/alexandria
/usr/lib/ruby/1.8/glib2.rb: line 55
GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
-----------------------
Alexandria just crashed
-----------------------
Timestamp: Tue Feb 06 09:06:41 CST 2007
Message: Not a book
Backtrace:
/usr/lib/ruby/1.8/alexandria/library.rb:66:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:53:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:52:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:92:in `loadall'
/usr/lib/ruby/1.8/alexandria/library.rb:86:in `loadall'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:266:in `load_libraries'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:84:in `initialize'
/usr/lib/ruby/1.8/alexandria/ui.rb:41:in `main'
/usr/lib/ruby/1.8/alexandria.rb:66:in `main'
/usr/bin/alexandria:10
Release: 0.6.1

Uname -a: Linux david-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
--
Please report this dump to 'alexandria-list@rubyforge.org' with some additional
information, such as the description of the crash and the steps to reproduce it
(if it's possible).
david@david-desktop:~$  


Any assistance will be deeply appreciated.  (BTW -- still a noobie in Ubuntu/Linux)

---

### Post by jazzman83 on 2007-03-12
I have this exact same error as you do and I run 64-bit Edgy.  I  was working for a while until I tried to upload my own book image and then it crashed and has never ran since.

I tried the following code which re installed all the ruby files but it didn't help me, 

sudo apt-get remove --purge alexandria
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install alexandria

---

### Post by skrimpy on 2007-04-15
A friend and I have been playing with Alexandria as well and really like it, though it is VERY buggy and I do wish it was still being developed.  It's an awesome program.

My friend had the same problem you guys have been having and I thought I'd let you know how he fixed it.

Navigate to your home folder and select View-->hidden files.  You should see a file .alexandria, which has all your book information in it.  Move to the library you were working when you crashed.  Your books are saved as text files in there by ISBN number.  If you were working with a particular book deleting its text file (and maybe image file too) should allow your program to restart.  My friend found this worked for him.  He said the text file was empty for that book and it seemed to be causing the program to crash repeatedly, before it ever launched.

I hope development of this is resumed, it's a cool program.

---

### Post by macallen on 2007-04-16
I found that having a 0 lenght .yaml file in my .alexandria directory would prevent alexandria from starting.

---

