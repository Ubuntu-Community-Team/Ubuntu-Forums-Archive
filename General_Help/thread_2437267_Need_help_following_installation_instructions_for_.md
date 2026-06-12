---
title: "Need help following installation instructions for TikZit"
date: 2020-02-20
forum: General Help
---

### Post by retsek2 on 2020-02-20
The README says:

This is a portable version of TikZiT 2.1. To launch TikZiT, simply run
'bin/tikzit'. To install launcher and icons for the current user, make
sure the 'bin' sub-directory is in your $PATH and run:

# ./install-local.sh

inside the tikzit directory.


TikZiT is released under the GNU General Public License, Version 3. See:

[http://tikzit.github.io](http://tikzit.github.io)

for full details and source code.

But I am not sure how to add the bin sub-directory to my $PATH

I want to be able to access TikZit from my application launcher

---

### Post by him610 on 2020-02-20
```

echo $PATH

```
Shows the current path. If you inspect it carefully, you will probably see that it is already in your path.

---

### Post by yancek on 2020-02-20
>  To launch TikZiT, simply run
'bin/tikzit'. 

Try: /bin/tizkit with the forward slash at the beginning then cd to the tikzit directory and run the install script.

---

### Post by retsek2 on 2020-02-21
> **yancek said:**
> Try: /bin/tizkit with the forward slash at the beginning then cd to the tikzit directory and run the install script.

When I run /bin/tikzit/ it runs the program but I don't want to have to open the program from my terminal every time. When I am running the program I can't call any commands in terminal pressing enter just makes a new line. If I run the install script (with the program running and when its not running) I looks like it runs correctly no errors occur but the program is still not accessible from my program launcher (even after restarting). 

> **him610 said:**
> ```

echo $PATH

```
Shows the current path. If you inspect it carefully, you will probably see that it is already in your path. 

My path is now:
/home/retsek/tikzit/bin:/home/retsek/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

Is that correct?

---

