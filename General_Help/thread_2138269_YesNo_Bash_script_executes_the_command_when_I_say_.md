---
title: "Yes/No Bash script executes the command when I say no?"
date: 2013-04-23
forum: General Help
---

### Post by Singtoh on 2013-04-23
Hello all,

I have been trying to find a solution for days and can't find it. I have tried a dozen yes/no scripts from various postings around but they all do the same thing. I am actually inserting the scripts into my script and no matter what I try, when the script asks me if I want to continue and I say no! it still executes the command. I am sure it must be something in my script allowing it to execute, but as I am not a coder, I don't know how to fix it. Been trying though but with no luck. Hers is the script anyway:

```

```function ask {
while true; do
if [ "${2:-}" = "Y" ]; then
prompt="Y/n"
default=Y
elif [ "${2:-}" = "N" ]; then
prompt="y/N"
default=N
else
prompt="y/n"
default=
fi
# Ask the question
read -p "$1 [$prompt] " REPLY
# Default?
if [ -z "$REPLY" ]; then
REPLY=$default
fi
# Check if the reply is valid
case "$REPLY" in
Y*|y*) return 0 ;;
N*|n*) return 1 ;;
esac
done
}```

```

and when I insert this into this part of my script:

```

```# System Info
function nfo {
INPUT=0
echo ''
echo 'What would you like to do? (Enter the number of your choice)'
echo ''
while [ $INPUT != 1 ] && [ $INPUT != 2 ] && [ $INPUT != 3 ] && [ $INPUT != 4 ] && [ $INPUT != 5 ] && [ $INPUT != 6 ] && [ $INPUT != 7 ] && [ $INPUT != 8 ] && [ $INPUT != 9 ] && [ $INPUT != 10 ] && [ $INPUT != 11 ]
do
echo '01. Software Versions?'
echo '02. Networking?'
echo '03. Graphics Card?'
echo '04. Audio?'
echo '05. Processor?'
echo '06. Memory?'
echo '07. Hdd Sdd?'
echo '08. USB Devices?'
echo '09. PCI Devices?'
echo '10. Hardware Overview?'
echo '11. Return?'
echo ''
read INPUT
# Software versions
if [ $INPUT -eq 1 ]; then
ask
    echo 'Running Versions...'
    cat /etc/issue
    uname -r
    uname -a
    gnome-shell --version
    echo 'Done.'
    nfo
# Networking
elif [ $INPUT -eq 2 ]; then
    echo 'Results...'
    lspci | grep Ethernet
    ifconfig
    iwconfig
    echo 'Done.'
    nfo
# Graphics Card
elif [ $INPUT -eq 3 ]; then
    echo 'Results...'
    glxinfo 
    glxinfo | grep render
    glxinfo | grep direct
    glxinfo | grep vendor
    lspci | grep VGA
    #glxgears
    xrandr
    echo 'Done.'
    nfo
# Audio
elif [ $INPUT -eq 4 ]; then
    echo 'Results...'
    lspci | grep Audio
    aplay --list-devices
    echo 'Done.'
    nfo
# Processor
elif [ $INPUT -eq 5 ]; then
    echo 'Results...'
    cat /proc/cpuinfo
    cat /proc/loadavg
    echo 'Press C key to sort processes'
    top
    echo 'Done.'
    nfo
# Memory
elif [ $INPUT -eq 6 ]; then
    echo 'Results...'
    cat /proc/meminfo
    free -m
    echo 'Press M key to sort processes'
    top
    echo 'Done.'
    nfo
# Hdd Ssd
elif [ $INPUT -eq 7 ]; then
    echo 'Results...'
    df -H
    echo 'Requires root privileges:'
    sudo fdisk -l
    echo 'Done.'
    nfo
# USB Devices
elif [ $INPUT -eq 8 ]; then
    echo 'Results...'
    lsusb
    echo 'Done.'
    nfo
# PCI Devices
elif [ $INPUT -eq 9 ]; then
    echo 'Results...'
    lspci
    echo 'Done.'
    nfo
# Hardware Overview
elif [ $INPUT -eq 10 ]; then
    echo 'Results...'
    hwinfo --short
    echo 'Done.'
    nfo
# Return
elif [ $INPUT -eq 11 ]; then
    clear && main
else
# Invalid Choice
    echo 'Invalid choice. '
    nfo
fi
done
main
}```

```

it executes even if i tell it no! I am trying this on non critical stuff like the above untill I can get it working correctly. The rest of the script has stuff like wipe devices, reset stuff,install stuff, delete stuff ect.ect. and that kind of thing. So it would be nice if this would work so I could have it say "Hey Bozo, Do you really want do do this" it actually does this now but still executes even when telling it no! Sorry for rambling and Thanks in advance for any help you could pass along.

Cheers,

Singtoh

---

### Post by Singtoh on 2013-04-23
Sorry for the above with no code tags, I tried twice to put them in and it did't work??

Cheers,

Singtoh

---

### Post by Vaphell on 2013-04-23
[****code] [/code] ?

---

### Post by Singtoh on 2013-04-23
Hello Vaphell,

Sorry, I tried that and it didn't work. See if this works??


```

```# Software versions
if [ $INPUT -eq 1 ]; then
ask
    echo 'Running Versions...'
    cat /etc/issue
    uname -r
    uname -a
    gnome-shell --version
    echo 'Done.'
    nfo
# Networking
elif [ $INPUT -eq 2 ]; then
    echo 'Results...'
    lspci | grep Ethernet
    ifconfig
    iwconfig
    echo 'Done.'
    nfo
# Graphics Card
elif [ $INPUT -eq 3 ]; then
    echo 'Results...'
    glxinfo 
    glxinfo | grep render
    glxinfo | grep direct
    glxinfo | grep vendor
    lspci | grep VGA
    #glxgears
    xrandr
    echo 'Done.'
    nfo
# Audio
elif [ $INPUT -eq 4 ]; then
    echo 'Results...'
    lspci | grep Audio
    aplay --list-devices
    echo 'Done.'
    nfo
# Processor
elif [ $INPUT -eq 5 ]; then
    echo 'Results...'
    cat /proc/cpuinfo
    cat /proc/loadavg
    echo 'Press C key to sort processes'
    top
    echo 'Done.'
    nfo
# Memory
elif [ $INPUT -eq 6 ]; then
    echo 'Results...'
    cat /proc/meminfo
    free -m
    echo 'Press M key to sort processes'
    top
    echo 'Done.'
    nfo
# Hdd Ssd
elif [ $INPUT -eq 7 ]; then
    echo 'Results...'
    df -H
    echo 'Requires root privileges:'
    sudo fdisk -l
    echo 'Done.'
    nfo
# USB Devices
elif [ $INPUT -eq 8 ]; then
    echo 'Results...'
    lsusb
    echo 'Done.'
    nfo
# PCI Devices
elif [ $INPUT -eq 9 ]; then
    echo 'Results...'
    lspci
    echo 'Done.'
    nfo
# Hardware Overview
elif [ $INPUT -eq 10 ]; then
    echo 'Results...'
    hwinfo --short
    echo 'Done.'
    nfo
# Return
elif [ $INPUT -eq 11 ]; then
    clear && main
else
# Invalid Choice
    echo 'Invalid choice. '
    nfo
fi
done
main
}```

```


and here is the yes/no function I am trying to get working:



```

```function ask {
    while true; do
 
        if [ "${2:-}" = "Y" ]; then
            prompt="Y/n"
            default=Y
        elif [ "${2:-}" = "N" ]; then
            prompt="y/N"
            default=N
        else
            prompt="y/n"
            default=
        fi
 
        # Ask the question
        read -p "$1 [$prompt] " REPLY
 
        # Default?
        if [ -z "$REPLY" ]; then
            REPLY=$default
        fi
 
        # Check if the reply is valid
        case "$REPLY" in
            Y*|y*) return 0 ;;
            N*|n*) return 1 ;;
        esac
 
    done
}```

```






Cheers,

Singtoh

---

### Post by Singtoh on 2013-04-23
Don't know. Code tage aren't going in for some reason, or I'm a braindead twit??

Sorry

Cheers,

Singtoh

---

### Post by Vaphell on 2013-04-23
[co****de] actual code [/code]


```
# Software versions
if [ $INPUT -eq 1 ]; then
ask
    echo 'Running Versions...'
    cat /etc/issue
    uname -r
    uname -a
    gnome-shell --version
    echo 'Done.'
    nfo
# Networking
elif [ $INPUT -eq 2 ]; then
    echo 'Results...'
    lspci | grep Ethernet
    ifconfig
    iwconfig
    echo 'Done.'
    nfo
# Graphics Card
elif [ $INPUT -eq 3 ]; then
    echo 'Results...'
    glxinfo 
    glxinfo | grep render
    glxinfo | grep direct
    glxinfo | grep vendor
    lspci | grep VGA
    #glxgears
    xrandr
    echo 'Done.'
    nfo
# Audio
elif [ $INPUT -eq 4 ]; then
    echo 'Results...'
    lspci | grep Audio
    aplay --list-devices
    echo 'Done.'
    nfo
# Processor
elif [ $INPUT -eq 5 ]; then
    echo 'Results...'
    cat /proc/cpuinfo
    cat /proc/loadavg
    echo 'Press C key to sort processes'
    top
    echo 'Done.'
    nfo
# Memory
elif [ $INPUT -eq 6 ]; then
    echo 'Results...'
    cat /proc/meminfo
    free -m
    echo 'Press M key to sort processes'
    top
    echo 'Done.'
    nfo
# Hdd Ssd
elif [ $INPUT -eq 7 ]; then
    echo 'Results...'
    df -H
    echo 'Requires root privileges:'
    sudo fdisk -l
    echo 'Done.'
    nfo
# USB Devices
elif [ $INPUT -eq 8 ]; then
    echo 'Results...'
    lsusb
    echo 'Done.'
    nfo
# PCI Devices
elif [ $INPUT -eq 9 ]; then
    echo 'Results...'
    lspci
    echo 'Done.'
    nfo
# Hardware Overview
elif [ $INPUT -eq 10 ]; then
    echo 'Results...'
    hwinfo --short
    echo 'Done.'
    nfo
# Return
elif [ $INPUT -eq 11 ]; then
    clear && main
else
# Invalid Choice
    echo 'Invalid choice. '
    nfo
fi
done
main
}
```


```
function ask {
    while true; do
 
        if [ "${2:-}" = "Y" ]; then
            prompt="Y/n"
            default=Y
        elif [ "${2:-}" = "N" ]; then
            prompt="y/N"
            default=N
        else
            prompt="y/n"
            default=
        fi
 
        # Ask the question
        read -p "$1 [$prompt] " REPLY
 
        # Default?
        if [ -z "$REPLY" ]; then
            REPLY=$default
        fi
 
        # Check if the reply is valid
        case "$REPLY" in
            Y*|y*) return 0 ;;
            N*|n*) return 1 ;;
        esac
 
    done
}
```


so what do you need? you want tu put ask() in every option before executing relevant block of code?

---

### Post by prodigy_ on 2013-04-23
Just want to suggest a different y/n function here.

```
#!/bin/sh

yesNo () {
	old_stty=$(stty -g)
	stty -icanon iuclc -echo min 1 time 0
	while :; do
		user_answer=$(dd bs=1 count=1 2>/dev/null)
		case $user_answer in
			y|n) 
				echo "$user_answer"
				ret_val=0
				test "$user_answer" = "n" && ret_val=1
				stty "$old_stty"
				return $ret_val ;;
			*)
				;;
		esac
	done
}
```

---

### Post by Singtoh on 2013-04-23
Hello Vaphell,

Yes, but when I do that the script runs and asks me the yes/no question, but when I say no to the question, it still executes as if I said yes.

Cheers

Singtoh

---

### Post by Singtoh on 2013-04-23
> **prodigy_ said:**
> Just want to suggest a different y/n function here.

```
#!/bin/sh

yesNo () {
    old_stty=$(stty -g)
    stty -icanon iuclc -echo min 1 time 0
    while :; do
        user_answer=$(dd bs=1 count=1 2>/dev/null)
        case $user_answer in
            y|n) 
                echo "$user_answer"
                ret_val=0
                test "$user_answer" = "n" && ret_val=1
                stty "$old_stty"
                return $ret_val ;;
            *)
                ;;
        esac
    done
}
```

Hello Prodigy,

I will give this a try, but I have tried many and they all seem to execute the script when I say no. I'll give it a go.

Cheers,

Singtoh

---

### Post by steeldriver on 2013-04-23
where are you actually testing the return value of the 'ask' function though? I'm not seeing it...

```
ask
if [ $? -ne 0 ]; then
  echo 'Negative, Ghost Rider'
else
  echo 'Go!'
fi

```

---

### Post by Singtoh on 2013-04-23
> **steeldriver said:**
> where are you actually testing the return value of the 'ask' function though? I'm not seeing it...

```
ask
if [ $? -ne 0 ]; then
  echo 'Negative, Ghost Rider'
else
  echo 'Go!'
fi

```

Hello steeldriver,

Not quite sure of what you mean. Sorry, I am not what any would even consider a novice at this code thing. I just try to cobble things together and hopefully can get something to work, but is this what you mean??

```
#Ask
function ask {
read -p "Are you sure you want to continue? <y/N> " prompt
if [[ $prompt == "y" || $prompt == "Y" || $prompt == "yes" || $prompt == "Yes" ]]
then
  exit 0
fi
}

```[/QUOTE]

And I can put "ask" anywhere in the script ahead of any command and it will ask me "Are you sure you want to continue? <y/N>" an when I type n or N, it just carries on executing the script instead of exiting.

Sorry, bear with me, a code guru I am not:(

Cheers,

Singtoh

---

### Post by Singtoh on 2013-04-23
> **steeldriver said:**
> where are you actually testing the return value of the 'ask' function though? I'm not seeing it...

```
ask
if [ $? -ne 0 ]; then
  echo 'Negative, Ghost Rider'
else
  echo 'Go!'
fi

```

It seems the same when I insert your code as well. When I say "n" it executes the script and I see this:

Go!
Running Versions...
Ubuntu 13.04 \n \l

3.8.0-19-generic
Linux singtoh-pc 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
GNOME Shell 3.8.1
Done.
Go!

for that particular bit of script??

Cheers,

Singtoh

---

### Post by Vaphell on 2013-04-23
> Not quite sure of what you mean. Sorry, I am not what any would even consider a novice at this code thing. I just try to cobble things together and hopefully can get something to work, but is this what you mean??

this is a very wrong approach. Unless it's a one time job and you are never going to code in bash again, i'd suggest you to actually learn and understand what you are playing with.
gluing some random code together won't make your script automagically work.

you need to have something that follows this logic
if <ask() returned OK> then
  do stuff
else
  do nothing


```
ask()
{
  read -p "Are you sure you want to continue? <y/N> " prompt;
  if [[ $prompt == "y" || $prompt == "Y" || $prompt == "yes" || $prompt == "Yes" ]]
  then
    return 0
  else
    return 1
   fi
}
```


```
$ if ask; then echo OK; else echo CANCEL; fi
Are you sure you want to continue? <y/N> y
OK
$ if ask; then echo OK; else echo CANCEL; fi
Are you sure you want to continue? <y/N> N
CANCEL
```

---

### Post by Singtoh on 2013-04-23
> **Vaphell said:**
> this is a very wrong approach. Unless it's a one time job and you are never going to code in bash again, i'd suggest you to actually learn and understand what you are playing with.
gluing some random code together won't make your script automagically work.

you need to have something that follows this logic
if <ask() returned OK> then
  do stuff
else
  do nothing


```
ask()
{
  read -p "Are you sure you want to continue? <y/N> " prompt;
  if [[ $prompt == "y" || $prompt == "Y" || $prompt == "yes" || $prompt == "Yes" ]]
  then
    return 0
  else
    return 1
   fi
}
```


```
$ if ask; then echo OK; else echo CANCEL; fi
Are you sure you want to continue? <y/N> y
OK
$ if ask; then echo OK; else echo CANCEL; fi
Are you sure you want to continue? <y/N> N
CANCEL
```

Good advice to be certain Vaphell. I am a bit too old to be playing around with this I guess, my memory isn't what it used to be. I don't know how you guy/girls remember all this code. I can hardly remember from one website to the next. Anyway, I guess I'll leave it be I was just kind of fiddling around anyway.:) Thanks Vaphell for the good advice and the help.:)

Cheers,

Singtoh

---

