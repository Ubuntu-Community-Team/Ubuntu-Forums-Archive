---
title: "Install of restricted extras was interrupted. Error shown..."
date: 2020-07-08
forum: General Help
---

### Post by Extreedoc on 2020-07-08
As above, I was installing Ubuntu restricted extras through the terminal when the process was interrupted; my fault I think. It got to the part where Microsoft was laying down the law about use of their fonts etc and it just seemed to hang at 33% It was getting late so I was forced to kill the process.

Error message is: Brokencount>0. unmet dependencies.
I tried to get into the package manager, to be met by this message: 
E:dpkg was interrupted. Manually run 'dpkg-configure-a' to correct the problem.
E_cache->open()failed. Please report.
Can somebody walk me through what I need to do?

---

### Post by ActionParsnip on 2020-07-08
Ok, run:
```

sudo dpkg-configure-a

```

What is the  output please? The system gave you the next command to run......

---

### Post by Extreedoc on 2020-07-08
It says "command not found"? I copied and pasted it from your post above to make sure of no errors.

---

### Post by deadflowr on 2020-07-08
Should be  spaces between dpkg and configure and -a
and configure should be double dashed
like
```
sudp dpkg --configure -a
```

---

### Post by Extreedoc on 2020-07-08
Thanks for the above, here is the output:

```
sudo] password for user: 
Setting up libvo-amrwbenc0:amd64 (0.1.3-2) ...
Setting up libmspack0:amd64 (0.10.1-2) ...
Setting up libaribb24-0:amd64 (1.0.3-2) ...
Setting up cabextract (1.9-3) ...
Setting up libavcodec-extra58:amd64 (7:4.2.2-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...

```

---

### Post by deadflowr on 2020-07-08
I'm guessing it ended up back at your user prompt.
So if you run
```
sudo apt update
sudo apt upgrade
```
does it still error?

---

### Post by Extreedoc on 2020-07-08
Ok, I've updated and upgraded and it asked me if I wanted to continue and I typed y and it's back to installing restricted extras. Fine, but it's back at the Microsoft warning page, (end user agreement etc) and it just sits there. I don't know what to do; is it expecting a response from me and if so, what?

---

### Post by deadflowr on 2020-07-08
Press tab and then arrow keys to toggle to the Ok (or yes) and accept the eula.

---

### Post by Extreedoc on 2020-07-08
Thanks, it seems to have worked ok this time, that end user page is a pain, I've never had to tab and arrow before and hope I got it right. At any rate, the 'error' icon has gone.
Thanks to all.

Edit: Just checked on the Synaptic and it's saying that the Ubuntu restricted extras isn't installed... comments? Should I try again using Synaptic instead of Terminal?

---

### Post by deadflowr on 2020-07-08
Post back what
```
dpkg -l| grep restricted
```
shows.

---

### Post by Extreedoc on 2020-07-08
This?

```
dpkg -l| grep restricted
ii  ubuntu-restricted-addons                   26                                    amd64        Commonly used restricted packages for Ubuntu

```

---

### Post by deadflowr on 2020-07-08
Interesting, it's basically half installed.

You can try
```
sudo apt install ubuntu-restricted-extras
```
or you can go ahead and see what happens if you try installing it through synaptic.

Your choice

You might need to do the tab selection again.

---

### Post by Extreedoc on 2020-07-08
I'll give her another go.

---

### Post by Extreedoc on 2020-07-08
That was much quicker and no Microsoft page this time. Synaptic shows it as installed this time.
Thanks Deadflowr

---

