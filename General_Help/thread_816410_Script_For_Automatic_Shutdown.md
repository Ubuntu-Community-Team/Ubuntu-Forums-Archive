---
title: "Script For Automatic Shutdown?"
date: 2008-06-02
forum: General Help
---

### Post by GCoffee on 2008-06-02
hello All,

I was thinking of running a server of some-sort on my computer - and from previous threads have heard that my pc can support the task. but I was wondering this:

In August I am going camping for 10 days - I have no friends who have enough technical know-how to ssh tunnel or anything so they can't monitor the server, so I was wondering if there was a script that turned off the pc as soon as it reached a certain temprature - say 65 celcius?

I don't have a internet connection or anything when camping.. So it could be difficult trying to monitor over the internet...

Cheers,
GCoffee.

---

### Post by pytheas22 on 2008-06-02
Most BIOS programs have an option to shut the machine down if it reaches a certain temperature.  If yours doesn't, then I'm sure you could write a script to do the same thing.  It would probably only take a few lines of bash.  But I'd check BIOS first, as that would be the easiest solution.

Of course, you should try to make sure your computer is not going over 65 degrees in the first place.  What kind of server are you trying to set up that makes you worry that the CPU will overheat, and what kind of CPU do you have?

---

### Post by GCoffee on 2008-06-02
I'm going to be running a - probably - light webserver.. I think it might overheat because its a seriously small room..

Its a intel pentium 4 processor if thats what you mean by cpu..

I checked bios - no shutdown feature there..

Can anyone write a bash script?

Cheers,
GCoffee.

---

### Post by ibuclaw on 2008-06-02
Yes, most BIOS settings have an emergency kill switch if the temperature reaches that high.

But it is very unlikely. It would only happen if a fan unexpectedly failed.
Else it'll have to take one huge giant cochroach getting jammed in the thing! :D

There is an app called "sensors" (from the package **lm-sensors** in Ubuntu. (**apt-get install lm-sensors** if you don't have it).

That will display all Temperature information.

And this line will show the current temperature.
```
export CPU=$(sensors | grep "CPU Temp" | awk '{print $3}') && echo ${CPU:1}
```

Regards
Iain

---

### Post by GCoffee on 2008-06-02
I know about the sensors package and such - but my system often reaches 65 celcius when active.. this is when running programs and such though - not just sitting there..

What help would the sensors package do though when I am about 150 miles away?

---

### Post by ibuclaw on 2008-06-02
[EDIT] Moved to new post
...
Although, perhaps for the nature of what you are asking.
You could run this script (or a script like this) as root before you leave...?
```

#!/bin/bash
while true
do export CPU=$(sensors | grep "CPU Temp" | awk '{print $3}')
   export CPU=${CPU:1} && export CPU=${CPU/.*}
# The above gets the temperature of the CPU.
   if [ $CPU -ge 65 ]
   then poweroff
# If the CPU Temp is 65 or over, then poweroff.
   else sleep 1m
# Else sleep for a minute before rechecking again.
   fi
done

```

---

### Post by GCoffee on 2008-06-02
Cheers,

That sounds like just the script i need, now how would you run it in terminal - and when I get back - how would i stop it?

---

### Post by ibuclaw on 2008-06-02
When connected to your server just run the file as such:
```
./script.sh &
```

And to kill it, when you re-connect to the server and type in:
```
killall script.sh
```
[EDIT]
Although, to poweroff, you need to be root, so you will have to execute both commands using **sudo**.

Regards
Iain

---

### Post by boterbram on 2008-10-26
Thanks a lot, I was looking to do exactly the same. I actually wanted to make the script myself, but then I figured I didn't really know how to. So ill now just have a good look at yours and see what you're doing

Thanks again!

---

