---
title: "Minecraft - Bukkit"
date: 2014-07-13
forum: General Help
---

### Post by taparius on 2014-07-13
Hello members.

I was looking at the bukkitwiki and noticed that what they have done there is not working for me. If anybody could help out and inform me of a simple way of setting up my own bukkit server on Kubuntu or simply clearify the instructions that would be amazing.
Thank you for any help.

---

### Post by ubudog on 2014-07-13
Hi,

What about the instructions are you having problems with?

---

### Post by taparius on 2014-07-13
Inside the instructions they say to make a folder "~/craftbukkit". I am wondering if they want me to make the server name ~/craftbukkit or just craftbukkit and ~/ is just a command. I'm sorry if this sounds stupid as I am a very new user to ubuntu. also when I try and run most of the commands in the instructions the terminal says file not found.

---

### Post by sandyd on 2014-07-13
> **taparius said:**
> Inside the instructions they say to make a folder "~/craftbukkit". I am wondering if they want me to make the server name ~/craftbukkit or just craftbukkit and ~/ is just a command. I'm sorry if this sounds stupid as I am a very new user to ubuntu. also when I try and run most of the commands in the instructions the terminal says file not found.

Which commands give you the error, and what page are you using.

You can create ~/craftbukkit by running
```

mkdir ~/craftbukkit
```

---

### Post by ubudog on 2014-07-13
```
mkdir ~/craftbukkit
```
would make a directory "craftbukkit" in the home directory of the user that you're logged in as. "~/" means "/home/username/".

As sandyd said, what specific commands are giving you the errors?

---

### Post by taparius on 2014-07-13
So I made the folder but I was wondering if by making a new file they just mean a ordinary geddit or text file? and then just type it in?

---

### Post by ubudog on 2014-07-13
By making a new file they probably mean just creating a file by the name they give you, so, for instance: "Create the file xyz with contents 'hello world'", you would "gedit xyz" from the terminal, and copy/paste "hello world" into it and save.

Can you post a link to the directions you're following and tell us what exactly you're having trouble with?

---

### Post by taparius on 2014-07-13
the command that game me trouble was the command to actually start the server. This command was ~/craftbukkit/craftbukkit.sh, I had used cd to go to my documents and access the ~/craftbukkit folder and made a geddit file with the required text in it but when I ran the command it just said 
"No such file or directory"

---

### Post by ubudog on 2014-07-13
It seems like you made a directory called "~/craftbukkit" in your Documents directory.  So, when you go to run "~/craftbukkit/craftbukkit.sh", you are running, "/home/username/craftbukkit/craftbukkit.sh", not "/home/username/Documents/~/craftbukkit/craftbukkit.sh" hence the "No such file or directory."

For your purposes, just replace "~/" with "/home/yourusername", and try starting the tutorial over again.

---

### Post by taparius on 2014-07-13
I re-wrote the command as such "/home/myusername/Documents/craftbukkit/craftbukkit.sh" but when I entered it I recieved 
"Error: Unable to access jarfile craftbukkit.jar" I'm not sure what to do. I tried changing the permissions, I am in root and have made all the files executable.

---

### Post by ubudog on 2014-07-13
Rewrite the command.  Can you post a link to the tutorial you're following?

---

### Post by ubudog on 2014-07-13
In response to your post #10 edit, looks like your jarfile is still located in your Documents directory, make sure that your .jar is in the right location for craftbukkit.sh to launch it.

---

### Post by taparius on 2014-07-13
My appologies it seems my internet went berzerk as I could not see your text. Also where should I leave the jar? [http://wiki.bukkit.org/Setting_up_a_server#Linux](http://wiki.bukkit.org/Setting_up_a_server#Linux) that is the link to the tutorial.

---

### Post by ubudog on 2014-07-13
No problem.

Ok, so let's see if I can simplify and clarify some things:
1. Create a directory, "craftbukkit" in your home directory ("/home/username/", also seen as "$HOME", or "~/")
```
mkdir ~/craftbukkit
```
this is the same as "mkdir /home/username/craftbukkit" or "mkdir $HOME/craftbukkit"

2. Change your directory to the craftbukkit directory you just created:
```
cd ~/craftbukkit
```
You should already be in your home directory when you start the terminal, so you could just do "cd craftbukkit", but we'll run this just to be sure.

3. Download the craftbukkit .jar.  You could download it from your browser, save it and move it to your ~/craftbukkit directory, or we could do it from the command like, like so:
```
wget http://dl.bukkit.org/latest-rb/craftbukkit.jar
```
Now, you should have the latest craftbukkit.jar file in your ~/craftbukkit directory.

4. Create your startup script (craftbukkit.sh).  This is a bash script that sets up some variables for java, so that it can run your Bukkit server properly.  You could type it by hand to start your server, but this just makes it easier.  For more on bash scripting, see [tldp.org's intro to bash]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html"), if you are interested.

Open it in gedit:
```
gedit craftbukkit.sh
```

Then paste the following:
> #!/bin/sh
 BINDIR=$(dirname "$(readlink -fn "$0")")
 cd "$BINDIR"
 java -Xmx1024M -jar craftbukkit.jar -o true

Now, make it executable:
```
chmod +x craftbukkit.sh
```

5. Start it up!
```
./craftbukkit.sh
``` or, when you first start your terminal, since you'll be in your home directory,
```
~/craftbukkit/craftbukkit.sh
```

Hope that clears things up, let me know if you have any questions!

---

