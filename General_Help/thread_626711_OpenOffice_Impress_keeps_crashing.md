---
title: "OpenOffice Impress keeps crashing"
date: 2007-11-29
forum: General Help
---

### Post by tak1150 on 2007-11-29
I've been a happy OO user for almost a year now.
Granted that I have not worked with this big of a presentation file before (~30MB), with OO 2.3, Impress keeps crashing every ~15-30 mins. This is just no acceptable. Is this because of Compiz Fusion, etc? I do not get any messages in the terminal even if I start it in the terminal.

Does anybody have the same problem? Has anybody figured out what causes this?

I have a Dell inspiron 1150 laptop w/ P4 2.8GHz and 1GB RAM. Thanks for your input.

Tak

---

### Post by forestpixie on 2007-11-29
have you tried changing the amount that oo uses for memory - in tools >options then the openoffice.org tab >memory

you could also run oo impress with the file and then open terminal and check top to see if it is a memory problem

or 

it could be that it's the ubuntu oo version causing you problems in which case you can install the openoffice one

---

### Post by tak1150 on 2007-11-29
> **forestpixie said:**
> have you tried changing the amount that oo uses for memory - in tools >options then the openoffice.org tab >memory

you could also run oo impress with the file and then open terminal and check top to see if it is a memory problem

or 

it could be that it's the ubuntu oo version causing you problems in which case you can install the openoffice one

Thanks for replying :)
I had changed the memory allocation to maximum (256MB).
After I posted here, I remembered there is a little bug associated with SCIM in Gutsy, so I turned it off and I have not had a crash for the last 30 min or so.

---

### Post by tak1150 on 2007-12-06
Well, it still crashes even with SCIM off.
Is there nobody else that is experiencing this?

---

### Post by forestpixie on 2007-12-06
have you tried installing the openoffice version - others have had some issues as well

---

### Post by tak1150 on 2007-12-06
> **forestpixie said:**
> have you tried installing the openoffice version - others have had some issues as well

No, I haven't. Would I have to uninstall the openoffice package first?

---

### Post by forestpixie on 2007-12-06
yes - when I've done I've searched synaptic for openoffice then clicked the 'S' in one of the columns - selected all the openoffice stuff - do a complete removal

last time I did it I used this page - [http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

I'm not saying that it's a certainty - but the gutsy version has a few bugs I've seen, I've got an annoying one on mine but it's not worth worrying about as it is.

---

### Post by tak1150 on 2007-12-06
> **forestpixie said:**
> yes - when I've done I've searched synaptic for openoffice then clicked the 'S' in one of the columns - selected all the openoffice stuff - do a complete removal

last time I did it I used this page - [http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

I'm not saying that it's a certainty - but the gutsy version has a few bugs I've seen, I've got an annoying one on mine but it's not worth worrying about as it is.

I uninstalled openoffice completely and installed the native package as you suggested. It does feel quite a bit snappier and faster. We'll see if I still have the crash problem. It's a bummer that I can't have the quickstarter, because I'd have to install openoffice-common and if I do, I'd replace all the native OO with Ubuntu OO. Also I don't like the native widgets, but oh well. I like performance better :) Thanks for your suggestion and help.

Tak

---

### Post by tak1150 on 2007-12-12
> **tak1150 said:**
> I uninstalled openoffice completely and installed the native package as you suggested. It does feel quite a bit snappier and faster. We'll see if I still have the crash problem. It's a bummer that I can't have the quickstarter, because I'd have to install openoffice-common and if I do, I'd replace all the native OO with Ubuntu OO. Also I don't like the native widgets, but oh well. I like performance better :) Thanks for your suggestion and help.

Tak

Yes, I still have the crash problem + animation in the slides are slow. The objects seem to hesitate before they move (same was true in Ubuntu OO). :(

---

### Post by bullon on 2008-06-02
my OO impress crashes as well, especially when I try to use 3d transitions (in this case it always crashes!)

---

