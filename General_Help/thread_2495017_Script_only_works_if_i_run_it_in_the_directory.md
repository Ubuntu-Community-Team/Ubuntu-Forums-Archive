---
title: "Script only works if i run it in the directory"
date: 2024-02-04
forum: General Help
---

### Post by jsnotlout on 2024-02-04
I have some scripts I use to start my server automaticaly. They used to work, Then I changed them to attempt to run as non root users. Since I didnt know how big a security risk that was till now. The problem is, when I run the script like this as root user:
I do cd /home/minecraft/CreeperVillage3
then i do runuser -u minecraft ./Start.sh

that works fine, However when I put this in a bash script, and run it nothing happens. It doesn't error or do anything I'm failing to see what is different. Arent they both in theory the same?
Contents: runuser -u minecraft /home/minecraft/CreeperVillage3/Start.sh

Im not great at linux so sorry for my awful mistakes lol.
Also I would post this on stack exchange but they bully and harras me for not knowing enough (no joke, I refuse to use that site ever again) 
If i shouldnt post this here, Im sorry. I ran out of places

Edit: Its running, as the discord notifications i put in are working. But the screen session either never starts or doesn't stay on, as it does not show up, and the server is not accessible

---

### Post by MAFoElffen on 2024-02-04
I would have to see the contents of /home/minecraft/CreeperVillage3/Start.sh to see if it uses relative or absolute path references. Then that "would" make a big difference in how that worked. That would be my first guess, without seeing that.

---

### Post by dragonfly41 on 2024-02-04
I am no expert in bash scripting but I usually give the script permissions to run by right clicking on Start.sh and changing from local user to run. But of course you must be very confident that the script comes from a reliable source by verifying. As regards  minecraft .. I would be cautious about the source. 

[https://www.reddit.com/r/bash/comments/159eajn/why_do_bash_scripts_need_to_have_permission/?rdt=51420](https://www.reddit.com/r/bash/comments/159eajn/why_do_bash_scripts_need_to_have_permission/?rdt=51420)

---

### Post by jsnotlout on 2024-02-04
The script came from me, I created it and know what it does. It has run permission

---

### Post by jsnotlout on 2024-02-04
This is all that I have in the script Start.sh script: screen -AmdS CreeperVillage3 java -Xmx5048M -Xmx5048M -jar paper-1.20.4.jar

I did however get this to work, i combined them as one single script, will this continue to work? Or is it flawed:
#!/bin/sh
runuser minecraft -l -c "cd /home/minecraft/CreeperVillage3/ && screen -AmdS CreeperVillage3 java -Xmx5048M -Xmx5048M -jar paper-1.20.4.jar"

---

### Post by MAFoElffen on 2024-02-05
This may sound too simple... Following the "Why change what works..." adage. 

You said the referred script runs fine if you manually change to the folder of the script first, before calling it.

Instead of coming up with a one liner, which you would do in a command line, you are using a script, so it doesn't matter how many lines you use to do it in... The script automates that process to save you that work. I sometimes, in my scripts, even span lines of a long command stream, so that it is more readable to others that might come upon it later, so they can follow the logic... 

Maybe you are overthinking this. Instead of doing that... Why not do the same as what works for you successfully in the command line, logically? 

Example:
```

#!/bin/bash

PWD=$(pwd)
cd /home/minecraft/CreeperVillage3/
runuser -u minecraft ./Start.sh
cd $PWD

```
Or expand it out to make it more flexible
```

#!/bin/bash

######
# VARS
######
PWD=$(pwd)
ARG1=$1
ARG2=$2
WF=/home/minecraft/CreeperVillage3/
User="minecraft"

###########
# Functions
###########
function CheckArgs {
  if [[ !z $ARG1 ]]
  then
    WF=$ARG1
  fi

  if [[ !z $ARG2 ]]
  then
    User=$ARG2
  fi
}

function StartIt {
  cd $WF
  runuser -u $User ./Start.sh
}

#######
# Main
#######
CheckArgs
StartIt

cd $PWD
exit 0

```

---

### Post by TheFu on 2024-02-05
> **jsnotlout said:**
> The script came from me, I created it and know what it does. It has run permission

This is usually due to parts of the script or config files assuming a specific PWD.  There are ways around this - the better is to ensure that every command inside the script will run without assuming any PWD.  Basically, configs and programs need to use absolute paths.

The not-so-great solution would be to add a **cd {assumed path}** to the top of the script to set the PWD.  The issue is that this will fail if the directory cannot be entered for any reason.  The risk for this could be tiny or huge.  Just depends what is inside the script.  For example, if there is any clean up that removes files and that part uses relative paths and the chdir fails, it is possible for the wrong files to be deleted.

Since you created the script, you'll know if there is any impact or not.

It is common for certain types of programs to have an expected PWD.  Webapps running outside apache (ruby, perl, python) are common.  Some Java programs care too, but there are others.  Did you set JAVA_HOME correctly?

---

