---
title: "Unity not working on start-up (12.04)"
date: 2013-02-01
forum: General Help
---

### Post by theo2409 on 2013-02-01
Hello!

I've been using ubuntu for 2 years but I'm still a beginner. I recently upgraded to 12.04 from 10.04 and things were fine until now. When I log in, unity is missing. I did a CTRL+ALT+T>'sudo unity' to restore it but it still looks and feels weird. 

Looks like I'm in some sort of ROOT safe mode cause Chromium won't start as ROOT but it asks to be started as a normal user. The guest account seems fine. 

Please help guys. I've tried searching for a solution, but none of them helped.  Thanks in advance!

---

### Post by Frogs Hair on 2013-02-01
Hello and Welcome 

Try CTRL+ALT+T ```
unity --reset
```

---

### Post by theo2409 on 2013-02-01
Hello! 

'Unity --reset' restores the original Unity panel but the terminal shows [this]("http://paste.ubuntu.com/1598148/")

---

### Post by Frogs Hair on 2013-02-01
Try restarting now or simply close the terminal

---

### Post by theo2409 on 2013-02-01
It still doesn't solve the problem. Is there a way to start or reset unity by default at startup?

---

### Post by Frogs Hair on 2013-02-02
You should not have to. Run the Unity support test and post the output.    ```
/usr/lib/nux/unity_support_test -p 
```
Install the following in case compiz needs reset.

```
sudo apt-get install dconf-tools
```

---

### Post by theo2409 on 2013-02-13
This is the output of /usr/lib/nux/unity_support_test -p


OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G41 x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

I have also installed dconf-tools

---

