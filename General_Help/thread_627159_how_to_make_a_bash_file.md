---
title: "how to make a bash file"
date: 2007-11-29
forum: General Help
---

### Post by twist2b on 2007-11-29
ok i just need to put this script in a bash file:

[PHP]compiz --replace[/PHP]

becuase even though compiz starts out AWSOME and perfectly smooth... as soon as i open something.... BAM, compiz fails on me, then i just type in the terminal
compiz --replace and its almost the same.... besides backround is a little messed up.....

ANYWAYS
how do i make a bash file so i can add it to
ence.

Thanks. Other than that it looks OK?
System>Prefrences>sessions>startup stuff......
i would really appreciate that....
OR you could tell me how to fix it from doing that :P either one is accepted!

---

### Post by CheShA on 2007-11-29
all you need to do is make a text file.


Start it with (must be the first line!)

```
#!/bin/bash
```

and end it with 

```
exit 0
```

then you need to 
```
chmod +x   /path/to/file/filename 
```

and then you can execute it


If you make the script  in somewhere like /usr/local/bin/ then you can execute it just by typing its name.

SOOOO 

If you did this:
```

sudo echo "#!/bin/bash" > /usr/local/bin/compizreplace
sudo echo "sleep 10"   >> /usr/local/bin/compizreplace
sudo echo "compiz --replace &" >> /usr/local/bin/compizreplace
sudo echo "exit 0" >> /usr/local/bin/compizreplace
sudo chmod +x /usr/local/bin/compizreplace

```

then you can add just the command "compizreplace" as a startup item and your compiz will be refreshed 10 seconds after you log in.

---

