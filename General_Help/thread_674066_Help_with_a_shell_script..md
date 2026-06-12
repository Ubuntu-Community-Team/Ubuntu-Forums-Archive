---
title: "Help with a shell script."
date: 2008-01-21
forum: General Help
---

### Post by Gerlads Mod on 2008-01-21
When I create this shell script it gives me errors and doesn't work.
My shell script is this:

```
#!/bin/sh
cd /home/USERNAME/Desktop/readbuttons
make
sleep 5
```

It doesn't work.
But if I run in terminal: 

```
cd /home/USERNAME/Desktop/readbuttons
make
```

It works. 
Any idea why it won't work in the script?

---

### Post by erginemr on 2008-01-21
Did you make your script executable:

```
chmod u+x your_script
```

---

### Post by Gerlads Mod on 2008-01-21
Yeah. Still gives me the same error.

EDIT:

It also works when I run it through terminal.
Like if I typed:

cd /home/USERNAME/Desktop/readbuttons
./mke.sh

It won't work if I double click it and hit run in terminal.

---

### Post by erginemr on 2008-01-21
Try:
./mke.sh

You need to specify to BASH that your script is in the same path as "./script_name". Otherwise, BASH will try looking for your script in the directiories defined by the $PATH environment variable.

---

### Post by Gerlads Mod on 2008-01-21
No I did that. Just forgot to type it on the forum.

No see I want it to work when I double click it and hit run in terminal.

It works any other way I try it. Just not the way I want it.

---

### Post by geirha on 2008-01-21
When you do that, the terminal will close immediately after make has run. Could that be the problem? or do you get any specific error messages?

Try adding a line with the command "read" at the end of your script. This will make the terminal stay open after make has run. Hitting enter will close it.

---

### Post by Gerlads Mod on 2008-01-21
That didn't help either.

And no the terminal doesn't close as soon as it's done because I have sleep 7. That makes it pause for 7 seconds then close.

Okay this is what it does when I run the script through terminal:

1. I open Terminal.
2. I type cd /home/USERNAME/Dekstop/readbuttons
3. I type ./mke.sh

Then it runs fine.
But when I try going in the readbuttons folder and click on mke.sh then Run in Terminal,
it gives me this:

```
make: psp-config: Command not found
makefile:12: /lib/build.mak: No such file or directory
make: *** No rule to make target `/lib/build.mak'.  Stop.
```

---

### Post by geirha on 2008-01-21
The first line of mke.sh, is it "#!/bin/sh"? If so, change it to "#!/bin/bash". This is obviously a path problem, and the path is probably set in one of bash's config files, which /bin/sh doesn't read.

---

### Post by Gerlads Mod on 2008-01-21
It still gives me the same error as before.
Even with #!/bin/bash

---

### Post by mali2297 on 2008-01-21
Instead of choosing *run in terminal*, try
```

gnome-terminal -e 'sh /path/to/yourscript.sh'

```

---

### Post by erginemr on 2008-01-21
I think the OP is dealing with PSP emulator programming. I have googled for the error he got:
```
make: psp-config: Command not found
makefile:12: /lib/build.mak: No such file or directory
make: *** No rule to make target `/lib/build.mak'.  Stop.
```

And the following post suggests exporting a path variable $PSPSDK or $PSPDEV:
[http://forums.ps2dev.org/viewtopic.php?p=54830&sid=d8368c2b03a1a5a4e93096656ba34a59](http://forums.ps2dev.org/viewtopic.php?p=54830&sid=d8368c2b03a1a5a4e93096656ba34a59)

So, I believe the OP should focus on manipulating path variables to get his script working:

---

