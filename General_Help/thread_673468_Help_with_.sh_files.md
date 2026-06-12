---
title: "Help with .sh files"
date: 2008-01-20
forum: General Help
---

### Post by Gerlads Mod on 2008-01-20
I have been using Ubuntu for over 1 month. I love it and I thought I should join this forum.
I just joined like 10 minutes ago so I am a n00b.

Anyway I scripted a lot of batch files when I was in Windows, and I want to make something like that. I searched and found that .sh files are similar to batch files.

I would like to know how to make a .sh file that runs a few commands.

I would like it to run the following in terminal and then close:

cd /home/USERNAME/Desktop/readbuttons
make
sudo cp EBOOT.PBP /media/disk/PSP/GAME150
sudo umount /media/disk

Thanks!

---

### Post by nick_h on 2008-01-20
Batch files in linux are called shell scripts.

You could put your commands in a file and then make it executable with:
```
chmod a+x filename
```
and then run it with:
```
./filename
```

A good place to start reading would be - [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by sumguy231 on 2008-01-20
You also need to begin the script with this line which tells the shell what to execute it with:
```
#!/bin/sh
```

---

### Post by LaRoza on 2008-01-20
See my wiki.

(In the Programming Library, under Operating Specific)

---

### Post by Gerlads Mod on 2008-01-20
Wait... I don't get this part.

If I want to check if a certain file exists how would I do this.

I know it's

```
if command here
then
command here
exit 1 
fi
```

But how would I check if a file is there or not.

---

### Post by nick_h on 2008-01-21
```
#!/bin/bash

if [ -e test_file ]; then
	echo "file exists"
else
	echo "file does not exist"
fi
```

In the link I gave you read the section "Flow Control - Part 1" under "Writing Shell Scripts".  You may want to use -f rather than -e.

---

### Post by cmnorton on 2008-01-21
> **Gerlads Mod said:**
> Wait... I don't get this part.

If I want to check if a certain file exists how would I do this.

I know it's

```
if command here
then
command here
exit 1 
fi
```But how would I check if a file is there or not.

First, here's one way to do it:

# check to see if file name supplied as first argument is present and readable
if [ -s ${1} ]; then 
  command1
  exit 1
fi

Second, there's nothing magic about naming shell scripts with a .sh extension. The magic is in two places: using chmod to set the script executable and putting the #!/bin/sh or #!/bin/bash as the first line of the script. 

If you are on RH-based systems, usually, /bin/sh is a link to /bin/bash. If you're on Debian, it's better to use #!/bin/bash, because /bin/sh is a link to /bin/dash which behaves differently than bash.

---

