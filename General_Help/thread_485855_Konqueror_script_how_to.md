---
title: "Konqueror script how to?"
date: 2007-06-27
forum: General Help
---

### Post by Naegling23 on 2007-06-27
Ok, so I would like to write a konqueror script, or something to that nature, but I have no idea how to do this.  To start off, Im trying to convert video for use in rockbox, which requires a specific framerate, and image size, as well as .mpg only.  I found a command that does this perfectly:

mencoder filename bunch of commands output_filename_.mpg

This command works great, however, in order to use it, I have to change the filename, and output file name, and enter it into the terminal.  I would really like to automate this process.  I was thinking something along the lines of right clicking on the file>actions>compress video and having everything done.  The problem is that I have zero ideas on how to go about this.  It seems like it should be simple, but I dont even know where to start, and googling "konqueror script how to" produces nothing.  To complicate things, my programming knowledge is about none, but I'm willing to learn.

Hopefully someone here can lend a hand.

---

### Post by eggdeng on 2007-06-27
The first thing you need to do is write a shell script. This basically means prepending```
 #!/bin/sh
``` to the top of a text file, adding the commands you want to run, saving the file and making it executable. Then you can run it from a terminal or make a launcher for it. If you need to specify input and output filenames, the terminal might be best. If you post the commands you want the script  to execute, I will try to help you out with it.

---

### Post by Naegling23 on 2007-06-27
here is the command

mencoder <input> -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=600 -vf scale,harddup -ofps 12 -zoom -xy 160 -o <filename>.mpg

Currently I have to manually change the input and filename by hand each time, which I'm trying to avoid.

thanks for the help

---

### Post by eggdeng on 2007-06-27
Copy and paste the following to a text file. 
```
#!/bin/sh
mencoder $1 -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=600 -vf scale,harddup -ofps 12 -zoom -xy 160 -o $2.mpg
```
As you can see, it just consists of your command with placeholders for the input and output filenames. Save it, for example as encode.sh (preferably to the folder where you keep your video files so as to avoid having to write long paths with the filenames) and make it executable ```
chmod +x /path_to_file/encode.sh.
``` You can now cd to the folder (you will need to have rwx permissions here) and call the script from the command line with two arguments, the first is the name of the input file and the second is the output file (this one, without the extension). ```
./encode.sh name_of_input_file name_of_output_file
```
Hope I have understood you right & that this is what you need.

---

### Post by Naegling23 on 2007-06-27
excellent, thanks for the help.  I was hoping to integrate this into konqueror so that all I would have to do is right click on a file, and convert it, but this is a step in the right direction.  Its easier than what I was doing.

---

### Post by Qu4k3R on 2007-06-28
[quote="me"][SIZE=1]
And don't forget to chmod it (to execute it) if needed.
:D[/SIZE]
[/quote]

[SIZE=3]
Then you can run the script by using:
bash <script>
sh <script>
[/SIZE]

---

