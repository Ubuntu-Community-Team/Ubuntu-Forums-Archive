---
title: "Bash scripts and Linux? I have absolutely no clue :("
date: 2014-02-18
forum: General Help
---

### Post by granthpark on 2014-02-18
I'd really like to install puush, but it's not officially released for Linux. This a really nice looking solution to my problem [https://github.com/blha303/puush-linux](https://github.com/blha303/puush-linux) but I don't really understand these simple instructions:
[LIST]
[*]Get puush from here: [https://github.com/blha303/puush-linux/raw/master/puush](https://github.com/blha303/puush-linux/raw/master/puush)
[*]Copy 'puush' to /usr/bin.
[*]Use it with puush file.name.
[/LIST]
Could someone tell me step-by-step how to execute these instructions?

---

### Post by Bucky Ball on 2014-02-18
*Thread moved to **General Help**.*

Nothing to do with ***Gaming & Leisure***.

Welcome. From your link:

> A Bash script for uploading files to puush.me from Linux. 

> Use it with puush file.name. 

If you want to upload, say,  picture1.jpg to puush.me, then you would use, in a terminal:

```
puush picture1.jpg
```

You would probably need to include the full path to the file, for instance:

```
puush /home/username/Pictures/picture1.jpg
```

... where 'username' is your username.

---

### Post by granthpark on 2014-02-18
Oh sorry for placing this in the wrong section. I'd like to know how to install puush though. Nonetheless, thanks for the response!

---

### Post by Bucky Ball on 2014-02-18
Ok, now I get you. I surmise you would open Leafpad (or your text editor of choice) and add this:

```
#!/bin/bash

PUUSH_API_KEY=""

if [ -z "$PUUSH_API_KEY" ]
then
echo "Set the variable PUUSH_API_KEY in $0 or with 'export PUUSH_API_KEY=\"apiKeyHere\""
  exit
elif ! [ -r "$1" ]
then
echo "Specify a file to be uploaded"
  exit
fi

curl "https://puush.me/api/up" -# -F "k=$PUUSH_API_KEY" -F "z=poop" -F "f=@$1" | sed -E 's/^.+,(.+),.+,.+$/\1\n/'
```

Save this file to /usr/bin as 'puush'. Then, open a terminal and issue:

```
sudo nano ~/.bashrc 
```

and at the end of the file add:

```
export PUUSH_API_KEY="apiKeyHere"
```

This bit in the last command "apiKeyHere" makes me think you should be putting a specific api key there, but I can't find one or any instructions about doing that, so I'm quite possibly wrong. Give it a try.

---

### Post by coldcritter64 on 2014-02-18
> **Bucky Ball said:**
> Ok, now I get you. I surmise you would open Leafpad (or your text editor of choice) and add this:

```
#!/bin/bash

PUUSH_API_KEY=""

if [ -z "$PUUSH_API_KEY" ]
then
echo "Set the variable PUUSH_API_KEY in $0 or with 'export PUUSH_API_KEY=\"apiKeyHere\""
  exit
elif ! [ -r "$1" ]
then
echo "Specify a file to be uploaded"
  exit
fi

curl "https://puush.me/api/up" -# -F "k=$PUUSH_API_KEY" -F "z=poop" -F "f=@$1" | sed -E 's/^.+,(.+),.+,.+$/\1\n/'
```

Save this file to /usr/bin as 'puush'. Then, open a terminal and issue:

```
sudo nano ~/.bashrc 
```

and at the end of the file add:

```
export PUUSH_API_KEY="apiKeyHere"
```

This bit in the last command "apiKeyHere" makes me think you should be putting a specific api key there, but I can't find one or any instructions about doing that, so I'm quite possibly wrong. Give it a try.
@ Buckey Ball, After saving to /usr/bin/puush, set as executable ? Or a permission denied error may occur.
```
sudo chmod +x /usr/bin/puush
```

Edit: and a big g'day from the Far North :)

---

### Post by Bucky Ball on 2014-02-18
Good thinking coldcritter and a big hello from Adelaide, South Australia. ;)

@granthpark: As coldcritter64 advises, try that command after saving the file you create.

---

### Post by granthpark on 2014-02-18
Ah thanks! I didn't know what to expect; puush doesn't work the same way on Linux as it does on Windows, unfortunately.

---

### Post by sunmock on 2014-05-05
I've been feeling the lack of puush on linux for a while so I decided to make my own script that'll pretty much replicate windows/mac push but on linux. It'll take a few minutes to set up and hopefully the instructions on the repo are clear enough, but in case they're a bit too complicated, I'll try my best to explain simply here :)

[LIST=1]
[*]Go here [https://github.com/sunmockyang/puush-linux](https://github.com/sunmockyang/puush-linux) 
[*]At the right side, press the **download zip** button to download 
[*]**Extract** the files to desktop or wherever for now 
[*]Open the file "puush" in whatever text editor you want (gedit is fine) 
[*]On the 3rd line, you'll see **PUUSH_API_KEY=""**, you need to get your **puush api key** from [http://puush.me/account/settings](http://puush.me/account/settings) (hover to display) 
[*]Copy that key and put it between the quotation marks in the line mentioned above, save and close file 
[*]Assuming you're using a recent ubuntu version, make sure you have **curl**, and **xclip** installed. (Open terminal, run *sudo apt-get install curl xclip*) 
[*]Copy the puush file to */usr/local/bin* directory. (in terminal *cd *to wherever you have *puush* and *sudo cp puush /usr/local/bin*) 
[*]Go to your **system settings**, navigate to keyboard > Shortcuts Tab press the + at the bottom to add a **custom keyboard shortcut** 
[*]You'll add 4 shortcuts for puushing desktop, area, window, file. Name each of them whatever you want, the commands are: 
[/LIST]

[LIST]
[*]**puush -a** (puushes desktop) 
[*]**puush -b** (puushes area) 
[*]**puush -c** (puushes current window) 
[*]**puush -d **(opens up a file menu to puush a file) 
[/LIST]

 11. Set the shortcut key for each of the commands. (You can use Ctrl + Shift + 2/3/4/U just like in Mac/Windows)
12. **Log out and back in** so the changes take place.

Using the shortcuts, take screenshots and upload them. Once its done uploading, it will copy the puush link to your clipboard (ctrl+v one not the mouse one)

That was a lot more wordy than a lot of people would need to read, but I wasn't sure of what your level of linux proficiency would be...
This is my first time contributing to the community so I hope I'm doing it right

---

