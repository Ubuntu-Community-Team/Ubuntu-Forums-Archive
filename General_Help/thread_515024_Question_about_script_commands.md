---
title: "Question about script commands"
date: 2007-08-01
forum: General Help
---

### Post by HarrisonHopkins on 2007-08-01
Okay, I have a script in my /usr/bin/ that starts a game in my /usr/games/. The game has commands for it to do certain things, such as start at a specific map, and I can't start them with the script in /usr/bin/. Is there a way that I can get the script in /usr/bin/ to give the commands that I put on it to the game in /usr/games/?

---

### Post by HarrisonHopkins on 2007-08-01
Now I bump it.

---

### Post by reckless2k2 on 2007-08-01
not sure what you're getting at but do you mean adding the "sleep" function to your script? you can add the sleep function after a command and then initiate another command. i think this might be what you mean.

---

### Post by Sayers on 2007-08-01
I think your question would be easily answered by reading the /game/ manual as it is not a Ubuntu question and you don't provide us the name it is quite hard to answer :)

---

### Post by HarrisonHopkins on 2007-08-01
Then I guess let me simplify it...

How can I make a script do something if a command (like -file) is appended to the end of it? Such as "script -file file.jpg"?

---

### Post by mpeters on 2007-08-01
> **HarrisonHopkins said:**
> Then I guess let me simplify it...

How can I make a script do something if a command (like -file) is appended to the end of it? Such as "script -file file.jpg"?

I'm not sure I correctly understand your question, but, if the script in /usr/bin is just a script you should be able to open it up in a text editor an add the options you want. If you have trouble knowing what to edit try posting the script on here.

---

### Post by HarrisonHopkins on 2007-08-01
Yes, I know how to open it up, but I don't know how to add those options. All it does right now is cd to a directory, and then run the game.

---

### Post by mpeters on 2007-08-01
> **HarrisonHopkins said:**
> Yes, I know how to open it up, but I don't know how to add those options. All it does right now is cd to a directory, and then run the game.

Just type in the options at the end of the command which runs the game. So if the script currently looks like this:

```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand

```

Edit it to read:
```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand -file file.jpg

```

if you want to provide the name of the file when you run it, rather than statically code it into the startup file you can use the following:

```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand -file $1

```

now when you run:

```

script file.jpg

```

$1 in the script will be replaced by file.jpg so the script will again run ./somecommand -file file.jpg. You can provide more arguments using $1 $2 $3 etc, where $1 is the first, $2 the second argument you pass to the script.

---

### Post by reckless2k2 on 2007-08-01
if you know the other commands, then add them to the script using sleep under each full command. the commands would have to exist outside the game. i think that is what you're asking.

---

### Post by HarrisonHopkins on 2007-08-01
> **mpeters said:**
> Just type in the options at the end of the command which runs the game. So if the script currently looks like this:

```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand

```

Edit it to read:
```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand -file file.jpg

```

if you want to provide the name of the file when you run it, rather than statically code it into the startup file you can use the following:

```

#!/bin/bash

cd /usr/games/somedirectory;
./somecommand -file $1

```

now when you run:

```

script file.jpg

```

$1 in the script will be replaced by file.jpg so the script will again run ./somecommand -file file.jpg. You can provide more arguments using $1 $2 $3 etc, where $1 is the first, $2 the second argument you pass to the script.

Ah... I don't think that would work. These commands don't have to be in any particular order, and they all won't be used at once.

---

### Post by HarrisonHopkins on 2007-08-01
Bump time.

---

### Post by bodhi.zazen on 2007-08-01
> **HarrisonHopkins said:**
> Bump time.

Bumping you won thread is not so cool.

1. You have been given a very nice set of instructions already ...

2. We are all volunteers here ...

3. If you would like assistance you will need to provide more details, not more bumps ...

What game ?

What commands are you trying to run ?

> **HarrisonHopkins said:**
> Ah... I don't think that would work. These commands don't have to be in any particular order, and they all won't be used at once.

Why did the advice you have been given not work ? did you try it ?

---

### Post by HarrisonHopkins on 2007-08-01
It will not work, because that assumes that the commands are in a certain order, and that all commands will be used. Usually, only one or two of the commands will be used. So, I it to where if the script recieves the following command

script -file file.ext

It will pass "-file file.ext" to the program. The simple $1 codes won't work. The commands do not have to be in the same order, and shouldn't have to be.

---

### Post by jyba on 2007-08-01
Try getopt or, if your script is in bash, the getopts builtin.

---

### Post by HarrisonHopkins on 2007-08-01
After reading up on it, it seems that getopt is exactly what I am looking for. However, I can't seem to be able to get it to work.  Is there any place that will show me simply how to use it?

---

### Post by jyba on 2007-08-01
Here are a couple of links to examples from the Advanced Bash Scripting guide; the first is for the external command **getopt**...
[http://tldp.org/LDP/abs/html/extmisc.html#GETOPTY](http://tldp.org/LDP/abs/html/extmisc.html#GETOPTY)

...and this next one uses the bash builtin **getopts**...
[http://tldp.org/LDP/abs/html/internal.html#GETOPTSX](http://tldp.org/LDP/abs/html/internal.html#GETOPTSX)

---

### Post by bodhi.zazen on 2007-08-01
[http://www.linux.com/articles/113836](http://www.linux.com/articles/113836)

[http://www.linux.com/feature/118031](http://www.linux.com/feature/118031)

---

### Post by HarrisonHopkins on 2007-08-01
Okay, so I understand how that is used now. What I still don't understand however, is to get it to use use long command names, with only 1 - infront of it. How in the script would I seperate long command names that don't have an argument?

---

### Post by jyba on 2007-08-02
Well, I couldn't get the bash builtin to work with long options, so here's getopt instead:

```
#!/bin/bash

if [[ $# -eq 0 ]]; then
    echo "Usage:    $(basename $0) -[apples,bananas,cherry-pie,damson-tart] ARGS..."
    exit 1
fi

TEMP=$(getopt --alternative "apples,bananas,cherry-pie,damson-tart" -- "$@")

eval set -- "$TEMP"

while true; do
    case "$1" in
        -apples)       echo "Option 'a' selected";  shift  ;;
        -bananas)      echo "Option 'b' selected";  shift  ;;
        -cherry-pie)   echo "Option 'c' selected";  shift  ;;
        -damson-tart)  echo "Option 'd' selected";  shift  ;;
        --)                                         shift  ;;
        *)                                          break  ;;
    esac
done

echo "Remaining arguments are: $@"
exit 0
```

---

### Post by jyba on 2007-08-02
HarrisonHopkins, this is a matter of script design. If you want to parse all the '-foo' options first, and whatever are left are ARGS, then the script above should help you out.

However, I've just been reading back over the entire thread trying to work out what it is you actually do want to do, (it's really difficult because of the lack of any script and the dirth of words that you have given us - [COLOR="DeepSkyBlue"]**note**: words may be confusing, code is crystal clear[/COLOR]).

So I'm totally guessing that you want to offer the game-player the option of maybe choosing the map, perhaps choosing the background music, possibly choosing the difficulty level, or, if they want, just choosing the defaults for some or all of these options. (So maybe those options should be written into the game rather than the startup script?) Anyway, based on my assumptions, your options and arguments to /usr/bin/start_game might be something like...
```
start_game -map-file ~/.my_game/maps/map_01 \
           -difficulty_level 3 \
           -music_dir ~/.my_game/music/plague_music/
```
...if that's the sort of thing you want to do then the script in my previous post won't help, because you will need to parse *pairs* consisting of an option followed by an argument...
```
-map-file           ~/.my_game/maps/map_01
-difficulty_level   3 
-music_dir          ~/.my_game/music/plague_music/
```
If that's what you want to do then tell us (there's an easy solution), if it's not then tell us what you *do* want to do. If you can be clear about what you want then you're in the right place to find someone who knows how to do it.

---

