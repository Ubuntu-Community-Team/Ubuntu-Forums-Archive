---
title: "Possible to connect to FreeNX on Ubuntu using just SSH login?"
date: 2006-09-14
forum: General Help
---

### Post by rick_1010 on 2006-09-14
I have been experiencing a lot of difficulty getting FreeNX to work successfully on Ubuntu. I have, however used it successfully on other distros so I know that it is possible and have seen other threads where people have gotten it to work, however none of the threads have answered the issue that I am having (Anyways no need to get into that here..)

The question I have for anyone who has used FreeNX before is:

Is it possible to login to FreeNX without using the client, to just do a regular remote SSH login under the name "nx"?

I have heard some things about the nxclient / freenx compatiblity, with the new client not working with the current FreeNX server on Ubuntu so I figure if I can just bypass this issue by logging in directly with SSH it could save a lot of headaches. Anyways, I am in the process of trying to do this but need to get the key off my other machine so I just thought I'd see if anyone has done it before.

Thanks

---

### Post by sLLiK on 2006-09-15
To my knowledge, no.  The compression and methods behind how NX works requires some sort of NX client to handle the interaction and output to your screen.  Much like how Microsoft's termserv client is required for remote GUI desktop interaction.  Utilizing a remote NX server's capabilities doesn't directly translate to firing up a remote X.  Someone who's more farmiliar with VNC versus FreeNX and more intimiately understands the differences might be able to explain it better (or refute me entirely).  :D

Now you CAN make it so that the initial login and all subsequent traffic are ssl-encrypted, but that's not the same thing as what you're asking.

---

