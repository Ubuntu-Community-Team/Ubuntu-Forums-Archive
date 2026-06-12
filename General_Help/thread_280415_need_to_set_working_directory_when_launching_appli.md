---
title: "need to set working directory when launching application"
date: 2006-10-19
forum: General Help
---

### Post by theslut on 2006-10-19
I am trying to get linux dc++ working from a launcher but it fails.

It will only run if i physically go into the directory and run it.

I think it because it looks for ./glade to run succesfully and this is in the linuxdcpp so it looks like the working directory is not set when running the executable file from the launcher.

I've now put my direcotry in /usr/lib and created a symlink to the executable in /usr/bin but it won't run unless i open the command and do a 

cd /usr/lib/linuxdcpp

any other messages tell me it can't find the glade files in ./glade.

How do i registered the working path or tell it where glade is?

---

### Post by theslut on 2006-10-19
ignore this.

i went through the install instructions properly and its ok now.

---

