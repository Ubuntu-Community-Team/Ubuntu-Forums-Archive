---
title: "Installing libstdc++5"
date: 2008-02-27
forum: General Help
---

### Post by Shinitenshi on 2008-02-27
Ok I have Natural Selection Server (Half LIfe MOD) and its giving me some errors:

Couldn't open file '/home/shinitenshi/servers/hlds/ns/addons/extralevels3/extralevels3_i386.so': libstdc++.so.6: cannot open shared object file: No such file or directory

So I looked around and they told me I needed to install the libstdc++5 which i have no clue how. can any one lead me to the right path :)

---

### Post by Xyhthyx on 2008-02-27
```
sudo apt-get install libstc++5 libstdc++6
```

That installs both libstdc++5 (the one they told you to install) and libstdc++6 (the one mentioned in the error). Get both to be sure.

---

### Post by Shinitenshi on 2008-02-28
Ok now that i upgraded ubuntu to the most recent one 7. something it gives me this error which i think its even worse lol because people cant join my server at all!

pipes.cpp (484) : Assertion Failed: bRet
pipes.cpp (536) : Assertion Failed: bRet
steamclient.cpp (371) : Assertion Failed: pClientPipe->BWriteAndReadResult( buf, bufRet )
steamclient.cpp (373) : Assertion Failed: bufRet.TellPut() == ( sizeof(HSteamUser) + sizeof(uint8) )

tried that command and i have it installed already. (new ubuntu version just installed)

shinitenshi@ubuntu:~/servers/hlds$ sudo apt-get install libstc++5 libstdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstc++5
shinitenshi@ubuntu:~/servers/hlds$

---

### Post by Frankly Francois on 2008-02-28
> **Shinitenshi said:**
> 
E: Couldn't find package libstc++5
shinitenshi@ubuntu:~/servers/hlds$

Actually, I think its saying that it can't locate it. It wasn't installed.
I found this post earlier because I needed libstdc++5 for epsx. I got the same error message. After taking a second look at the command I see that it was missing a "D" in libst**d**c.

So try this.

```
sudo apt-get install libstdc++5 libstdc++6

```

Thank-you, Xyhthyx! :guitar:

---

