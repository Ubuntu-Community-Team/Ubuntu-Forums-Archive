---
title: "Can't make file executable script????"
date: 2014-09-18
forum: General Help
---

### Post by PopsTheSailor on 2014-09-18
I have a file that I've used the chmod +x on to make it executable and it doesn't work. Does the file need to be in a certain folder or can it be anywhere? I've tried the following variations:

chmod +x wifiredo
sudo chmod +x wifiredo
sudo chmod a+x wifiredo
sudo chmod +x wifiredo.sh

I also used Nautilus and checked the permissions. It's set to run as an executable. 

When I run it under all the above circumstances, I get wifiredo: command not found

---

### Post by steeldriver on 2014-09-18
```

command not found

```
is not an error about permissions - it simply means that the command is not found in your executable PATH - you need to specify the path explicitly, e.g. if it is in your current directory then prepend the relative path ./

```

./wifiredo

```

or put it somewhere that *is* on your PATH e.g. ~/bin (for personal executables) or somewhere like /usr/local/bin (for system-wide executables).

---

### Post by PopsTheSailor on 2014-09-19
Thanks. That did the trick. After verifying the ./ worked, I put the file in the usr/local/bin folder and it now works without ./

Marking this one solved.

---

