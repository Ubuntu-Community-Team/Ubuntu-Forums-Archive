---
title: "How to record the Terminal printout on a file ?"
date: 2023-08-26
forum: General Help
---

### Post by satimis on 2023-08-26
Hi all,

How to record the Terminal printout on a file ?

The Firefox browser freezes occasionally.  Only its window is not working(freezing), clicking on it with mouse pointer without response.  The OS is not freezing, still working.  I can logout and re-login the OS to restart Firefox.  Then Firefox works normal again.

I'm trying to find the cause of its freezing and running following command on Terminal;```

$ ./path/to/firefox-folder/firefox-bin | tee ~/output-a.txt

```
(Start Firefox browser on Terminal and pipe the printout on Terminal to output-a.txt file.)

It only works once with all printout recorded on output-a.txt file.   "tee ~/output-b.txt (output-c.txt/output-d.txt etc)" doesn't work any more after restarting the OS and Firefox browser.  Only an empty file is created

I couldn't resolve the problem.  Please help?

Thanks in advance.

Regards

---

### Post by Holger_Gehrke on 2023-08-26
A normal pipe only gets the standard output (file descriptor 1 in the shell) but errors and problems usually result in output to standard error (file descriptor 2). So to catch all the output you might want to try to send standard error to standard output before the pipe
either with '2>&1 |' or the shorthand '|&'. Alternatively there's the 'script' command for capturing a transcript of a shell session, but this captures everything including control sequences so the result might be difficult to read.

Holger

---

### Post by satimis on 2023-08-26
> **Holger_Gehrke said:**
> A normal pipe only gets the standard output (file descriptor 1 in the shell) but errors and problems usually result in output to standard error (file descriptor 2). So to catch all the output you might want to try to send standard error to standard output before the pipe
either with '2>&1 |' or the shorthand '|&'. Alternatively there's the 'script' command for capturing a transcript of a shell session, but this captures everything including control sequences so the result might be difficult to read.

Holger
Hi Holger,

Thanks for your advice.

I have tried
```

./path/to/firefox-folder/firefox-bin |& tee ~/output.txt

```

and ```

./path/to/firefox-folder/firefox-bin 2>&1 | tee ~/output.txt

```

before posting, also only an empty file created.

"script" will record everything and there will be a big output file resulted.

Regards

---

### Post by TheFu on 2023-08-26
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
Re-read that every year. There's always something new to learn that you weren't ready to learn in the prior years reading it.

---

### Post by MAFoElffen on 2023-08-27
> **Holger_Gehrke said:**
> A normal pipe only gets the standard output (file descriptor 1 in the shell) but errors and problems usually result in output to standard error (file descriptor 2). So to catch all the output you might want to try to send standard error to standard output before the pipe
either with '2>&1 |' or the shorthand '|&'. Alternatively there's the 'script' command for capturing a transcript of a shell session, but this captures everything including control sequences so the result might be difficult to read.

Holger

```

script --t=script_log -q scriptfile

```
Will record a terminal session until the User presses <Cntrl><D>

Here is how I handle redirection in my scripts to debug logging
```

logger() 
{
    logfile=$HOME/$sname.log
    case "$3" in
        1)
            exec 3>&2     # logging stream (file descriptor 3) defaults to STDERR
            ;;
        2) 
            exec 3>> $logfile     # send to log file
            ;;
        3)
            exec 3>&2 | tee $logfile     # send to both logfile and screen
            ;;
        *)
            echo -e "Something went wrong. Log option out of range."
            ResetLocale
            exit 1
            ;;
    esac
    
    
    if [ $verbosity -ge $1 ]; then
        # Expand escaped characters, wrap at 70 chars, indent wrapped lines
        echo -e "$startt $2" | \
            fold -w70 -s | \
            sed '2~1s/^/  /' >&3
    fi
}

```

---

### Post by satimis on 2023-08-27
> **TheFu said:**
> [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
Re-read that every year. There's always something new to learn that you weren't ready to learn in the prior years reading it.
Hi TheFu,

Thanks for your URL.  I'll look at it later.

Firefox installed on firefox-116.0.3.tar.bz2 seems quite stable now without freezing.  I'm testing it on my spare PC.

I run following command on Terminal to start Firefox;```

$ ./Downloads/Firefox/firefox/firefox-bin | tee ~/output_20230827a.txt

```

output_20230827a.txt is an empty file but there is output on Terminal;```

Missing chrome or resource URL: chrome://browser/skin/aboutSessionRestore-window-icon.png
Missing chrome or resource URL: chrome://browser/skin/abyss/img/waterfox-abyss-preview.svg

```

I'm interested to find out WHY the 1st time running;```

$ ./Downloads/Firefox/firefox/firefox-bin | tee ~/output_20230824.txt

```
output_20230824.txt is NOT an empty file?  Printout on Terminal is continue recorded on the file.

I attach the file output_20230824.txt here.  It is not an empty file.

Why all siminar commands run on Terminal later the output_date.txt is only an empty file?  Output on Terminal is not recorded on the file?

Regards

---

### Post by satimis on 2023-08-27
> **MAFoElffen said:**
> ```

script --t=script_log -q scriptfile

```
Will record a terminal session until the User presses <Cntrl><D>

Here is how I handle redirection in my scripts to debug logging
```

logger() 
{
    logfile=$HOME/$sname.log
    case "$3" in
        1)
            exec 3>&2     # logging stream (file descriptor 3) defaults to STDERR
            ;;
        2) 
            exec 3>> $logfile     # send to log file
            ;;
        3)
            exec 3>&2 | tee $logfile     # send to both logfile and screen
            ;;
        *)
            echo -e "Something went wrong. Log option out of range."
            ResetLocale
            exit 1
            ;;
    esac
    
    
    if [ $verbosity -ge $1 ]; then
        # Expand escaped characters, wrap at 70 chars, indent wrapped lines
        echo -e "$startt $2" | \
            fold -w70 -s | \
            sed '2~1s/^/  /' >&3
    fi
}

```
Hi MAFoElffen,

Thanks for your advice

I'll test it later.  Whether run following command on Terminal; ```

$ ./Downloads/Firefox/firefox/firefox-bin | script --t=script_log -q scriptoutput_date.txt

```
???

Pls advice;
Where shall I save your script?
What format will be the script? 
How to run the script to check scriptoutput_date.txt file?

I'll perform the test on the Firefox of my daily working PC.  The Firefox was installed on Ubuntu repository but how to start it on Terminal?

Thanks

Regards

---

### Post by yancek on 2023-08-27
I don't have any information on the script but you can start firefox in a terminal by typeing either?   /usr/bin/firefox OR firefox

---

### Post by Holger_Gehrke on 2023-08-27
'script' starts a new shell whose standard file descriptors are all redirected to get "caught" by script. So you just run 'script path-and-file-to-write-to' and then run 'firefox' in the new shell.

Holger

---

### Post by MAFoElffen on 2023-08-27
> **Holger_Gehrke said:**
> 'script' starts a new shell whose standard file descriptors are all redirected to get "caught" by script. So you just run 'script path-and-file-to-write-to' and then run 'firefox' in the new shell.

Holger
Yes... You start that, and do everything there, before you do anything else... to record everything "within" that shell.

If you do it like you tried in your post, then it would open a 'recorded shell session' [COLOR=#ff0000]after[/COLOR] the other initial process has already started. That doesn't work and would capture 'nothing'. 

Does that make sense to you now?

The code I posted is "BASH", which is just CLI commands with a few extensions. Use the commands from what I posted there just as "examples" on what you can try. When I do debugging of my scripts and applications, I include that code to capture what is going on, to send to debug logs, when I need to. I implement ways to do that from start options to turn it on, and to vary what it can do, based on what I need to see. (Basically, BASH is just commands.) 

You do not put it in a script to do what you need to do. You would just use those as example in your cli command for redirection. My comments in that code explains what it is doing for redirection. 

That is why I posted that...

---

### Post by TheFu on 2023-08-28
There are tools that specifically record terminal sessions for playback later as well.  I used them for presentations to ensure the demo-gods didn't destroy my live demonstrations.   Er ... because they weren't live, but just looked as if they were.  I haven't been giving live presentations away from home the last few years and I've wiped and upgraded my remaining computers since then, so I'm not certain I could find the tools.  Give me a second ... 

```
== Recording and replaying terminal session ==

use asciinema.  It embeds the timing information into the recording fi  le.
$ asciinema rec mystuff.ae
$ asciinema play mystuff.ae
$ asciinema upload mystuff.ae
 See below for more details on web publishing asciinema for replays.


```
== OR ==
```
#######################
The timing file is mandatory. scriptreplay doesn't work without it.

#  Record terminal session w/ timings
SCRIPT="name"
script --timing $SCRIPT.time $SCRIPT.log
script --timing $SCRIPT.time $SCRIPT.log

Using .time and .log are MY conventions. Not required, just useful.

#######################
#  Replay session w/ timings
scriptreplay  --timing $SCRIPT.time $SCRIPT.log

```
asciinema can be setup on a webpage for playback.  So if you've ever seen websites where it appears someone is typing in a terminal, they may be using asciinema.

Lots of ways to accomplish this.

---

### Post by satimis on 2023-08-28
Hi all,

**On my daily working PC**

**[COLOR="#FF0000"]Firefox of firefox-116.0.3.tar.bz2 started on Terminal[/COLOR]**
freezes a while and closes.

Following output found on Terminal;```

Missing chrome or resource URL: chrome://browser/skin/abyss/img/waterfox-abyss-preview.svg
[GFX1-]: GFX: RenderThread detected a device reset in PostUpdate
Exiting due to channel error.
Exiting due to channel error.
.....

```

There is no update available.

Please advise how to fix the problem?  Thanks

Regards

---

