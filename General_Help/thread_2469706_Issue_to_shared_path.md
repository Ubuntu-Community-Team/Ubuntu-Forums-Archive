---
title: "Issue to shared path"
date: 2021-12-07
forum: General Help
---

### Post by peter-1984 on 2021-12-07
Hi,
I did set up Samba to share the path on the machine with IP below. But I cannot access it with path like "\\113.255.223.181\sh_path" remotely.

---

### Post by QIII on 2021-12-07
There is an issue with your path if that is actually how you are entering it, but let's get to that later.

By what mechanism are you attempting to get to that directory and from what OS on the client?

---

### Post by peter-1984 on 2021-12-07
It's a Windows client. The same way did work fine with other machines.

---

### Post by peter-1984 on 2021-12-07
Waiting for your further advice

---

### Post by QIII on 2021-12-07
When adding the address of the Samba server/share in Add Network Location, did you use back slashes?  If so, use slashes just as you would as a URL.  Windows will interpret it with the back slashes, which you should see in the dialog where you are asked to name your location.

---

### Post by QIII on 2021-12-07
Also, can you ping the IP?

---

### Post by peter-1984 on 2021-12-07
Yes, I can ping the IP and cannot access it like the following.

\\113.255.223.181\sh_path

---

### Post by QIII on 2021-12-07
You are trying to map it as a network drive?

---

### Post by GhX6GZMB on 2021-12-07
> **peter-1984 said:**
> Yes, I can ping the IP and cannot access it like the following.

\\113.255.223.181\sh_path

Shouldn't it be : //113.255.223.181/sh_path

---

### Post by QIII on 2021-12-07
> **ml9104 said:**
> Shouldn't it be : //113.255.223.181/sh_path

Now that the OP has explained that they are working from a Windows machine, it will appear to that machine with back slashes.  When the network drive is mapped, normal slashes should be used.

But trying to connect from Windows, the user should be looking for the path with back slashes.  I added a network location with normal slashes, which now appears to the Windows machine thus:

[ATTACH=CONFIG]289601[/ATTACH]

This makes me wonder ... can you find \\113.255.223.181 -- without the path to the share?

---

### Post by peter-1984 on 2021-12-07
I used Windows to access it. This is why I've used 

\\113.255.223.181

Now I cannot access the above. If Samba is working fine, I can access the same shared path on other Ubuntu machine.

---

