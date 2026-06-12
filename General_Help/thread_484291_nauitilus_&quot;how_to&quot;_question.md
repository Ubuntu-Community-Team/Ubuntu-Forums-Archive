---
title: "nauitilus &quot;how to&quot; question"
date: 2007-06-25
forum: General Help
---

### Post by akajonesy on 2007-06-25
ok, I apologize in advance for this question as it's probably already been answered but I just have not been able to find the answer.

How can I get nautilus to ask for my password when I want to do something requiring "sudo" access?
According to how I understood the manual, if I tried to move files requiring permission (say to a protected drive) I should get something asking for password, or a drop down menu permitting it or something (I always imagined it would be like when I do updates or install programs, a window opens asking for password and off I go).
But so far the only way I can copy to protected files is by going to terminal and typing sudo nautilus. (which I imagine isnt the safest given how I don't know how to log off sudo after Im done).

So... can anyone please tell me how to get nautilus to transfer files between protected drives without going to terminal? 

Thanks

---

### Post by AlexThomson_NZ on 2007-06-25
That would be some cool functionality (asking for password) when trying to copy to r/o directory- is this being implemented?

I have a launcher on my taskbar which executes "gksudo nautilus", I just click on this whenever I need to access r/o files to save doing the console thing (quite handy)

---

### Post by akajonesy on 2007-06-25
Well thing is, I read in one of the manuals something about Nautilus doing something like that.
I'm moving some files to an external drive and it's secured, so I can do it with the sudo command, but otherwise it says Im not permitted to write to that disk.
I'd like to have temporary access to that drive in cases like this. 
For example, I drag the file to the folder in question, if its restricted I get asked for password, the action is done and back to secured mode. (as opposed to having to log in under sudo).
I'm trying to find the manual I read it in (read several books on ubuntu, so can't remember which it was in)soon as I find it Ill post, maybe Im misremembering.

---

### Post by fragos on 2007-06-26
You can do this with a nautilus script.  Create the following text file with a name like "Open as Administrator" and save it in ~/.gnome2/nautilus-scripts.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

Now when you right click a file or folder in nautilus, select Scripts then "open as Administrator".  You will be prompted for the password and the file will be opened with the application dictated by mime type as administrator.

---

