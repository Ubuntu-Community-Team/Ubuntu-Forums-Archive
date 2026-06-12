---
title: "Return variables with a bash scrips"
date: 2016-03-25
forum: General Help
---

### Post by bigmonmulgrew on 2016-03-25
So as I've got more and more scripts on my ubuntu server its become more common for me to call one script from another so I dont have to repeat code.

Then one day I wanted to get a variable from one bash scrip into the once calling it.

A little googling revealed you cant return a variable with bash so somthing like this wouldnt work

```
returnedvar=myotherscript
```

Seems bash can only return 0 or 1, failed or successful.

So here is how I decided to solve the problem. I wrote this little script first
```
#!/bin/bash

function return
{
	#Pass a variable  to be stored in "returned.var" or optionally use a name for the variable.
	if [ -z "$2" ]
	then
		filename="returned"
	else
		filename=$2
	fi
	
	echo "$1" >~/bin/$filename.var
	
	if [ ! -z "$3" ]
	then
		exit
	fi
}

#To test this out comment out this line and uncomment all the ones below it
return $1 $2 $3

#localvariable=235

#echo "Time to return a variable saved in returned.var"
#return $localvariable

#echo "Time to return a variable saved in myglobal.var"
#return $localvariable myglobal

#echo "Time to return a variable saved in myglobal.var and exit the script when returning"
#return $localvariable myglobal 1

#read -rsp $'You shouldnt see this message, Press any key to continue...\n' -n1 key
```

This file gets placed in ~/bin/returnvar. You cant call it return because that is in use already.
This is going to save the variable in a returned.var file in your home/bin directory. so any time you want to return a variable you use teh return comman. You can optionally specifty the variable name and if return should exit the script.

Then when we want to recover out variable we do 
```
retrievedvar=$(<~/bin/returned.var)
```

Lastly this si going to leave a lot of junk .var files in our bin directory so next we create this script
```
#!/bin/bash

#I use files in ~/bin/*.var to store varriables and return them form a bashscript
# This script ensures they get cleaned up

rm /home/admindm/bin/*.var

```
This deletes all the .var files in our bin directory. You can call this at the end of your scripts during cleanup but I've set mine to run on server reboot

```
sudo ln -s /home/admindm/bin/clean-variables.sh /etc/rc6.d/K99clean-variables
```
You could also do it on server shutdown or startup too if you like.

So what do you guys think to my solution to returnign variables?
I'm not exactly a linux pro so I'd be interested to see what the hardcore bash coders out there think

---

### Post by TheFu on 2016-03-27
No. Bash can return a 32-bit integer, so that is many, many return values, not just good (0) or bad (non-zero).
[https://www.linuxjournal.com/content/return-values-bash-functions](https://www.linuxjournal.com/content/return-values-bash-functions)
The ABSG is a great resource whenever doing something non-trival. [http://www.tldp.org/LDP/abs/html/assortedtips.html#MULTIPLICATION](http://www.tldp.org/LDP/abs/html/assortedtips.html#MULTIPLICATION) Basically, you have the output from the function echo'd and capture that, then parse the output into the variables as needed. Much cleaner, IMHO.

Of course, many admins switch to a different language whenever things get complicated - perl, python, etc.  I do when a bash script is longer than 1 page - perl is my choice (20+ yr user).  YAPC::NA is in Orlando this year (June) and there are almost free scholarships for anyone new to perl to attend - 3 days of conference, 3 nights hotel, and a beginning Perl5 training for $50. Apply on the YAPC::NA website.

---

### Post by bigmonmulgrew on 2016-03-27
Ah that sounds pretty cool. If it wouldn't cost me a grand in flights I would be very interested in that.

I guessed the articles I found googling were not telling the full story. Partly the reason I opened this thread was to get the discussion going.

---

### Post by HermanAB on 2016-03-27
Basically, at the end of a function, you can output a value with echo, then read it into a variable in the parent script or pipe it into the next thing and if you have to use temporary files, put them in /tmp, then they will eventually disappear when the system restarts.

You can also echo one value to stderr and another to stdout.  There are many more simple tricks.

---

### Post by bigmonmulgrew on 2016-03-27
I know putting them in tmp will make them disapper, dont know why I didnt think of that at the time, doh

Surely if I'm using echo to pass variables I will have issues if I echo more than once

---

### Post by SeijiSensei on 2016-03-27
You can use export to pass the values of environmental values between scripts.  I just tested it with this script, testpass1, that calls testpass2 in the same directory.

testpass1
```

#!/bin/bash

export TEST="Hello, world!"

./testpass2

exit 0

```

testpass2
```

#!/bin/bash

echo $TEST

exit 0

```
When testpass1 is run, "Hello, world!" is displayed on the console.

Using export puts the TEST variable into the environment for testpass2.

---

### Post by papibe on 2016-03-27
Another alternative: using the standard output to return values. Limited to non interactive scripts with no redirection:

script1.sh:
```
#!/bin/bash

var1="value"
var2=33

echo "$var1 $var2"

```
script2.sh:
```
#!/bin/bash

return_vars=$(./script1.sh)

for var in $return_vars; do
    echo "$var"
done

```
Then:
```
~$ ./script2.sh 
value
33

```
Just an idea. Hope it helps.
Regards.

---

### Post by bigmonmulgrew on 2016-03-28
Thanks guys I appreciate all the answers. AS I said before I mostly posted this to open the discussion. Figured there must be a lot of way to do this even though my quick google search said otherwise

---

