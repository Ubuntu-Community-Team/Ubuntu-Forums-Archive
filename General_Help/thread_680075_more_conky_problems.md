---
title: "more conky problems"
date: 2008-01-27
forum: General Help
---

### Post by JohnnyBoy022 on 2008-01-27
Im running conky on Ubuntu 7.10 with compiz-fusion. If I type "conky" in the terminal to start it everything works. When I close the terminal conky also closes. I am guessing this is because when it starts, conky says it is a "sub-window of the current window." How can I make it not a subwindow so when i close the terminal conky stays open?

Also if I add conky to the sessions start up list it has a gray shadow around it. I have looked into this and it is compiz that is putting the shadow there because conky is starting too soon. I tried changing the command in the sessions start up list to "sleep 15 && conky" but then conky doesn't start.

---

### Post by jpeddicord on 2008-01-27
Try starting it by hitting Alt+F2 and typing in conky. It should load up fine. As for the session bug, I'm not sure how to delay it.

---

### Post by taurus on 2008-01-27
Try

```
nohup conky
```
Now, see if conky's still there when you close the terminal.

---

### Post by JohnnyBoy022 on 2008-01-27
Thanks both of those solutions worked perfectly. Do you know if I am using the right command for the session start up list?

```
sleep 10 && conky
```

---

### Post by seventhc on 2008-01-27
to have conky start with a delay at start up do this.
```
#!/bin/bash
sleep 15 && conky;
```this will have it start after 15 seconds, you can change it to whatever you think you need.
save it as .conky_start.sh  (notice the period..this makes it a hidden file)
then in terminal
chmod a+x .conky_start.sh
chmod 755 .conky_start.sh (not sure if you need to do this one)
then in you session add /home/yourusername/.conky_start.sh

---

### Post by torgrot on 2008-01-27
I found a little script that I use to start conky that works just fine.
```

#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
fi
exec conky -d

```

I called it restart_conky.sh  and added it to my sessions.  Works like a charm.  I can restart after editing my .conkyrc file to see the effects.

torgrot

---

### Post by JohnnyBoy022 on 2008-01-27
Thanks, seventch, worked like a charm.

---

