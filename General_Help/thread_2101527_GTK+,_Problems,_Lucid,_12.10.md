---
title: "GTK+, Problems, Lucid, 12.10"
date: 2013-01-04
forum: General Help
---

### Post by endive71 on 2013-01-04
I've playing with C++ for a while, and I wanted to write programs that use GUI windows. So I tried to install GTK+ on Lucid Lynx. GTK+ had dependencies, so I tried to install the required packages in the correct order. It was pretty much the same for all of the packages. Download it, then run ./configure then make then make install.

glib installed ok.
ATK was the second dependency to install. I tried to install it. The console suggested running ldconfig. After I ran ldconfig, big problems started. All the open windows froze up, so I tried a restart. I was never again able to boot into the GUI interface. I could use CTRL+ALT+F1 to get a command line session. F2-F6 worked also. But CTRL+ALT+F7 for GUI session didn't work. I tried a command line session to copy my important files over to my Windows partition, but for some reason cp would only copy single files, not whole directories.

My home folder has it's own hard-drive partition, so I installed
Ubuntu 12.10 (Quantal Quetzal), and my files were all still there in the home folder.

Now that Quantal is installed, it is unreliable. It doesn't always boot. Sometimes I boot, restart, boot again, and then it works. Also, there are strange wireless networking problems. I can't get the wireless to work even though the computer claims to have a linux-broadcom driver installed.

Ubuntu 12.10 is a bit confusing.
Scrolling features I used to count on don't work. I can't use the mouse wheel to change tabs in the file browser. I also can't use the mouse wheel to scroll through months in the calendar that comes out of the clock.

I will probably switch back to Lucid Lynx.

-----
Main Questions:
-Why did things go haywire after ldconfig?
-Did I mess something up with my GTK experiment such that even new installations of Ubuntu malfunction?
-Do I need to reformat my /home hard drive partition? (I already reformatted the / partition.)
-What can I do to get started with GUI programming, in C++ or other languages, without killing my operating system?
-Why didn't cp copy folders?

My Hard Drive
ext3 /
ext3 /home
ntfs /Windows_XP
swap

---

### Post by endive71 on 2013-01-06
No replies yet?

Did I post too much or in the wrong place?

---

