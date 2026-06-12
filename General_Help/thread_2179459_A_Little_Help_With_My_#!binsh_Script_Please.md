---
title: "A Little Help With My #!/bin/sh Script Please"
date: 2013-10-08
forum: General Help
---

### Post by MrGrumpyArse on 2013-10-08
************************************************************** PLEASE SKIP TO 1ST REPLY FOR A MORE CONCISE QUESTION ***************************************************************************************


Hi I have been trying to write a shell script, the only true purpose of which is to learn the basics of writing a shell script, although it does attempt to address a physical issue on one of my Ubuntu installs.

**A bit of back ground -** 
The script is being tested on  Ubuntu-Gnome 13.10 64 bit (beta) running Gnome shell 3.10.  
This system is strictly speaking just a spare disk on pc configured to multi-boot between Ubuntu-Gnome 13.04, Win 7 (for my sons games :-( , and Ubuntu-Gnome 13.10 / Gnome-shell 3.10. 
 _It is installed merely to mess about with and hopefully learn something along the way, without the risk of killing anything important. _ 

**The issue the script attempts to address -**
After a lot of reading and searching I have now managed to get "13.10" to suspend and resume although Gnome-Shell 3.10 likes to crash on resume occasionally ( but thats not the issue I`am attempting to tackle, as suspending and resuming from the terminal pretty much works around that one )
The issue is that (as I understand it) the "network-manager" doesn't suspend properly and so often isn`t functioning after resume. (I have tried various tutorials that are intended to work around this with limited success).  So this has given me an _excuse _to "attempt" to write a script that "works around" this issue.

**How the script is intended to work -**
Basically all the script does is, on resume it pings  1. localhost   2. my router &  3. a web address.  It saves the exit code from each ping as a individual variable (exit code of 0 means that the ping attempt was successful) It then adds the variables together, then if the total is > 0, it restarts the network manager and begins the ping process again.  This can be repeated up to 3x before the script "gives in".  If / when the exit code totals = 0 the script also exits.
Stdout and stderror are redirected to a hidden file (which looks a bit messy!) before the last part of the script uses "grep" to put it into some sort of easy to read format.

[B]The problem- 
[/B]Despite my lack of any real scripting knowledge - Despite the fact that the script is probably an ugly monstrosity - Despite the fact the script could probably be written by "someone who knows what they are doing" in a couple of lines - Despite all this and more, In testing it pretty much does as well as I could expect (considering) and basically works _when executed from the terminal_.  Pulling out the appropriate Ethernet cable from my network switch provokes the desired output / reaction, likewise manually removing the DSL line from the router.   
The issue comes when it is run "on resume", I can get the script to run by putting it in "/etc/pm/sleep.d" and adding a couple of lines at the beginning to make it only run on resume. (or at least thats what I think is happening)  - BUT - the ping commands to my router and to a web address always returns  " connect: Network is unreachable"  despite the ping to localhost appearing to be successful (which to my limited knowledge suggests the network-manager is up and running)

So there you go - I am now at a point where I would appreciate a nudge in the right direction.

Whilst all advice and suggestions are appreciated - my hope is to make this version of my script work using things I can understand, before attempting to make it more correct and efficient using commands I don`t yet understand :-)

Apologies for being so long winded



Here is the script - comments were to help me understand what was happening, so may be wrong or misleading

```

#!/bin/sh                             
WEB=212.58.244.69            # www.bbc.co.uk
ROUTER=192.168.0.1         # localhost = 127.0.0.1
LOOP=3                             # edit this for number of times to run this script before giving in !
ATTEMPTS=0
LIMIT=1000
LOGFILE=/home/mark/Active-scripts/logs/unmms.txt           # file path to logfile
HIDLOGFILE=/home/mark/Active-scripts/logs/.unmms.log    # file path to hidden logfile
PREFIX="<> "                                                                   # prefix to put at the start of all lines echo'd to hidden logfile - script greps to $LOGFILE before closing.
PINGLOCALTEXTGOOD="Success - Localhost access ok"
PINGLOCALTEXTBAD="Error - Localhost access failed"
PINGLANTEXTGOOD="Success - L.A.N access ok"
PINGLANTEXTBAD="Error - L.A.N access failed"
PINGWEBTEXTGOOD="Success - WEB access ok"
PINGWEBTEXTBAD="Error - WEB access failed"
NMRESTART="Restarting network-manager \n <> \n <>"
NMOK="Full network access available - Nothing to do - Exiting script"
COMPLETE="The script has completed successfully \n <> \n <> \n <>"
NMFAIL="Network issue - Unable to reconnect all connections - Exiting script"
SPACE2="\n \n"
SPACE3="\n \n \n"




#case "$1" in                                                                               # these lines to run on resume when placed in /etc/pm/sleep.d
#    hibernate|suspend)
#    ;;
#    thaw|resume)
#    sleep 5
     
    
    exec 1>>$HIDLOGFILE 2>&1                                                  # redirects/appends stdout and stderr to variable / file




    while [ $ATTEMPTS -lt $LOOP ]; do                                       # while loop that runs up to 3x
        echo $SPACE3
    
        ping -c 1 -i 1 -W 2 -q localhost                                            # ping router (-c 1 ) = x1     (-i 1) = at 1 second intervals     ( -q) = output summary only
        LOCALEXITCODE=$?                                                      # Saves the exit code of the last run command "ping $ROUTER" as the variable "LANEXITCODE"
        sleep 10                      
        if [ $LOCALEXITCODE = 0 ]                                             # test to see if "ping router" was successful - ping returns exit code 0 for success
            then PINGLOCALTEXT=$PINGLOCALTEXTGOOD       # sets the variable PINGLANTEXT dependant on exit code from "ping $ROUTER" command
            else PINGLOCALTEXT=$PINGLOCALTEXTBAD
        fi
        echo $SPACE2
    
    
    
        ping -c 1 -i 1 -W 2 -q $ROUTER                                         # ping router (-c 1 ) = x1     (-i 1) = at 1 second intervals     ( -q) = output summary only
        LANEXITCODE=$?                                                          # Saves the exit code of the last run command "ping $ROUTER" as the variable "LANEXITCODE"
                              
        if [ $LANEXITCODE = 0 ]                                                # test to see if "ping router" was successful - ping returns exit code 0 for success
            then PINGLANTEXT=$PINGLANTEXTGOOD               # sets the variable PINGLANTEXT dependant on exit code from "ping $ROUTER" command
            else PINGLANTEXT=$PINGLANTEXTBAD
        fi
        echo $SPACE2
        
                                     
        ping -c 1 -i 1 -W 2 -q $WEB
        WEBEXITCODE=$?                                                      # Saves the exit code of the last run command "ping $WEB" as the variable "WEBEXITCODE"
    
        if [ $WEBEXITCODE = 0 ]                                             # test to see if "ping router" was successful - ping returns exit code 0 for success
            then PINGWEBTEXT=$PINGWEBTEXTGOOD           # sets the variable PINGLANTEXT dependant on exit code from "ping $ROUTER" command
            else PINGWEBTEXT=$PINGWEBTEXTBAD
        fi
        echo $SPACE2
    
    
        FULLACCESS=$(($LANEXITCODE+$WEBEXITCODE+$LOCALEXITCODE))   # Adds contents of the 3 variables together
    
        # echo $FULLACCESS
        DATETIME=$(date +"%c") 
        echo $PREFIX $DATETIME
        echo $PREFIX $PINGLOCALTEXT
        echo $PREFIX $PINGLANTEXT
        echo $PREFIX $PINGWEBTEXT    
        echo $SPACE2
    
    
        if [ $FULLACCESS -gt 0 ]                               # checks $FULLACCESS (comb total of exit codes from ping tests) - anything greater than 0 shows network error
            then echo $PREFIX $NMRESTART            # prints "restarting network-manager text"
            sudo restart network-manager                     # restarts network-manager
            sleep 2                                                      # pauses script to allow network-manager to restart
            else echo $PREFIX $NMOK                       # prints "network ok - nothing to do" text"
            ATTEMPTS=$((ATTEMPTS+1000))            # adds 1000 to $ATTEMPTS if $FULLACCESS = 0
    
        fi    
    
    
        ATTEMPTS=$((ATTEMPTS+1))                        # adds 1 to the variable $ATTEMPTS
    done




    # echo $PREFIX "Number of attempts - " $ATTEMPTS         # DEBUG LINE TO REMOVE **********************
    # echo $PREFIX "Loop - " $LOOP                                        # DEBUG LINE TO REMOVE **********************






    if [ $ATTEMPTS -ge $LOOP -a $ATTEMPTS -lt $LIMIT ]          #detects if $ATTEMPTS is => $LOOP and < $limit                      
        then echo $PREFIX $NMFAIL                                             #(true=echo $NMFAIL false= continue script 
    fi
    


    echo $PREFIX"------------------ END OF SCRIPT -------------------------- \n \n \n"




    grep $PREFIX $HIDLOGFILE > $LOGFILE




#;;
#esac



```


Run from terminal - network-manager running, produces (un-formatted output) the lines prefixed with <> are what show in the formatted version

```

PING localhost (127.0.0.1) 56(84) bytes of data.

--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.041/0.041/0.041/0.000 ms


 


PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.


--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.747/0.747/0.747/0.000 ms


 


PING 212.58.244.69 (212.58.244.69) 56(84) bytes of data.


--- 212.58.244.69 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 27.808/27.808/27.808/0.000 ms


 


<> Tue 08 Oct 2013 12:04:22 BST
<> Success - Localhost access ok
<> Success - L.A.N access ok
<> Success - WEB access ok


 


<> Full network access available - Nothing to do - Exiting script
<> ------------------ END OF SCRIPT -------------------------- 

```


Run on resume from " /etc/pm/sleep.d" produces (again unformatted)

```

PING localhost (127.0.0.1) 56(84) bytes of data.


--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.041/0.041/0.041/0.000 ms


 


connect: Network is unreachable


 


connect: Network is unreachable


 


<> Tue 08 Oct 2013 10:48:39 BST
<> Success - Localhost access ok
<> Error - L.A.N access failed
<> Error - WEB access failed


 


<> Restarting network-manager 
 <> 
 <>
network-manager start/running, process 28796


 
 


PING localhost (127.0.0.1) 56(84) bytes of data.


--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.039/0.039/0.039/0.000 ms


 


connect: Network is unreachable


 


connect: Network is unreachable


 


<> Tue 08 Oct 2013 10:48:49 BST
<> Success - Localhost access ok
<> Error - L.A.N access failed
<> Error - WEB access failed


 


<> Restarting network-manager 
 <> 
 <>
network-manager start/running, process 28811


 
 


PING localhost (127.0.0.1) 56(84) bytes of data.


--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.044/0.044/0.044/0.000 ms


 


connect: Network is unreachable


 


connect: Network is unreachable


 


<> Tue 08 Oct 2013 10:48:59 BST
<> Success - Localhost access ok
<> Error - L.A.N access failed
<> Error - WEB access failed


 


<> Restarting network-manager 
 <> 
 <>
network-manager start/running, process 28826
<> Network issue - Unable to reconnect all connections - Exiting script
<> ------------------ END OF SCRIPT -------------------------- 
 

```



I am now going to sit in a darkened room and rock back and forth gently awaiting inspiration....

Thanks in advance

Mark

---

### Post by MrGrumpyArse on 2013-10-09
[FONT=arial][SIZE=2]Ok after some further experiments and testing I am coming to the following generalised conclusions -

In order to get any script to run "on resume" the script needs to be put  /etc/pm/sleep.d  with a variation of the following code, dependant on if you want the script to run "on suspend" or "on resume"

[/SIZE][/FONT]```
[FONT=arial]case "$1" in[/FONT]
[FONT=arial]   hibernate|suspend)
  # *stuff to do on suspend *[/FONT]
[FONT=arial]   ;;[/FONT]
[FONT=arial]   thaw|resume)[/FONT]
[FONT=arial]  #*stuff to do on resume*[/FONT]
[FONT=arial]   ;;[/FONT]
[FONT=arial]esac[/FONT]

```[FONT=arial][SIZE=2]

Now what I believe is happening with my script is it is executed during resume - but before "some required part of the system" has loaded/resumed.

You can prefix the scripts file name with a number between 0 - 49 . 0 runs 1st during suspend and last during resume.  Giving the script various different number prefixes, and then checking "/var/log/pm-suspend.log" confirms that the script runs later the lower the number it is given.

But what ever number it is given it would appear to my mind, that the "resume process" waits for the script to finish before completely finishing.

Substituting my script for a simple "ping command script" seems to confirm this behaviour, always returning  "[COLOR=#000000]connect: Network is unreachable" [/COLOR][COLOR=#000000]regardless of the [/COLOR][COLOR=#000000]number it is prefixed with.  Adding a sleep command to the "simple ping script" still produces the same error, but delays the resume process by approx the same time as is given in the sleep command.[/COLOR]

[COLOR=#000000]Likewise replacing the script with a one that purely starts a second script stored in my home directory has the same results.  The "starter script" waits for the "main script" to finish before allowing the resume process to complete.[/COLOR]


[COLOR=#000000]So what I believe I need is -
[/COLOR]
[COLOR=#000000]A way to trigger my script that does not hold up the resume process, possibly a "starter script" (whatever the correct term is for such a thing) within "/etc/pm/sleep.d/"  that launches the main script but doesn't wait for it to complete, so allowing the resume process to complete before the bulk of the "main script" is run.  I could then adjust the sleep time within the "main script" so it runs just after the "resume process" completes?

Does anyone know how to do this? or have any alternate suggestions?  

Currently looking at the exec command here - [http://stackoverflow.com/questions/11183805/run-bash-script-from-another-script-without-waiting-for-script-to-finish-executi](http://stackoverflow.com/questions/11183805/run-bash-script-from-another-script-without-waiting-for-script-to-finish-executi)on but but (1). Im not sure if this does what I want & (2). I cant seem to get the exec command to run a simple script [/COLOR][/SIZE]:confused:

Thanks in Advance

Mark.[/FONT]

---

### Post by MrGrumpyArse on 2013-10-09
Success !!!!

Method - starter script in /etc/pm/sleep.d

```
 
#!/bin/sh
MAINSCRIPT=/home/mark/Active-scripts/network-manager_monitor_script_beta1

case "$1" in
        # hibernate|suspend)
    # ;;
    thaw|resume)                     # on resume only
    exec $MAINSCRIPT &      # launches $MAINSCRIPT but doesnt wait for it to finish (as would be normal) -
;;                                          # otherwise resume is paused until the script completes - $MAINSCRIPT requires -
esac                                     # the resume to complete before running!

```

I am away now to dance around the room singing " who`s the Daddy"  lol   - well it has taken me about 3 days - ah the joy of learning ..........

---

### Post by philinux on 2013-10-09
Well done. I'm running 13.10 and resume from suspend reconnects just fine here on an Acer 1410. Even xchat picks up where it left off.

Wonder if this is hardware dependant.

---

### Post by MrGrumpyArse on 2013-10-09
Cheers philinux

The irony is once I had started trying to write the script, I refused to run any updates until the script was able to do what I intended, just in case the updates fixed the issue before I could finish my work around!

The issue could be hardware dependent as I`m running this on an old-ish, home built quad core system that has an Nvidia chipset.  There is (last time I looked) a known bug related to the chipset which prevents the system from suspending

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840)   ( I think thats the correct link)

I have implemented the work around and now it suspends ok. 

Mark

Edit - just realised the network-manager issue only seems to occur when suspend is activated from the gui, not when suspending from the terminal. So perhaps a Gnome-shell 3.10 issue.........

---

