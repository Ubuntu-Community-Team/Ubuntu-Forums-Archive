---
title: "bash: My program exits instantly"
date: 2015-07-14
forum: General Help
---

### Post by spbach1234 on 2015-07-14
I am trying to make a program too boot and control a server on my network,  but when it starts it closes imidately when i added the check if y key pressed code.
I have etherwake installed.
```

#!/bin/bash
echo "Alive Check"
if ping -c 1 10.0.0.18 &> /dev/null
then
echo "Server is ON"
sleep 5
echo "Opening SSH Connection..."
ssh test@10.0.0.18
echo "Connection terminated"
read -p "Press any key to exit"
else
echo "Server is off"
read -p "Would you like to turn it on? Press Y" istrue
if [ istrue == 'y']
then
    wakeonlan 00:11:22:33:44:55
    echo "Powering on..."
    echo "Waiting for bootup..."
    while ! ping -c1 10.0.0.18 &>/dev/null; do :; done
    sleep 10
    echo "Boot Successful"
    echo "Opening SSH Connection..."
    ssh test@10.0.0.18
    echo "Connection terminated"
    read -p "Press any key to exit"
else
    read -p "Press any key to exit"
fi


```
Thanks

---

### Post by nerdtron on 2015-07-14
Shouldn't it be:
if [ $istrue == 'y']

---

### Post by steeldriver on 2015-07-14
... it also needs space before the closing ]

... and you have 1 more `if` than `fi` I think (consistent indentation would help spot things like this)

---

### Post by nerdtron on 2015-07-14
Oh and don't forget to run your script using bash  -x so that you'll see step by step on which part the script executed or had errors.
```
 bash -x ./myscript
```

---

### Post by spbach1234 on 2015-07-14
Thanks, my problem was i was missing a 'fi'

Ok, now this happens when i press any key

[B]Alive Check
Server is off
Would you like to turn it on? Press y y
/home/sam/Desktop/Server.sh: line 14: [: ==: unary operator expected
Press any key to exit

[/B]My code is
```

#!/bin/bash
echo "Alive Check"
if ping -c 1 10.0.0.18 &> /dev/null
then
echo "Server is ON"
sleep 5
echo "Opening SSH Connection..."
ssh test@10.0.0.18
echo "Connection terminated"
read -p "Press any key to exit"
else
echo "Server is off"
read -p "Would you like to turn it on? Press Y" $istrue
if [ $istrue == 'y' ]
then
    wakeonlan 00:06:5B:84:58:2C
    echo "Powering on..."
    echo "Waiting for bootup..."
    while ! ping -c1 10.0.0.18 &>/dev/null; do :; done
    sleep 10
    echo "Boot Successful"
    echo "Opening SSH Connection..."
    ssh test@10.0.0.18
    echo "Connection terminated"
    read -p "Press any key to exit"
else
    read -p "Press any key to exit"
fi
fi


```

---

### Post by nerdtron on 2015-07-14
I saw this on the net, it's probably worth a try. [http://stackoverflow.com/questions/11373702/a-simple-if-else-bash-script-which-reacts-to-users-yes-no-input](http://stackoverflow.com/questions/11373702/a-simple-if-else-bash-script-which-reacts-to-users-yes-no-input)

```

read -p "Run command $foo? [yn]" answer
if **[[ $answer = y ]]** ; then
  # run the command
fi 
```

---

### Post by papibe on 2015-07-14
Hi spbach1234.

'read' is not done correctly. There should be no '$' preceding the variable name:
```

read -p "Would you like to turn it on? Press Y" **[COLOR="#FF0000"]$[/COLOR]**istrue
                                                ^
```
Then the error:
```
[: ==: unary operator expected
```
comes from the 'istrue' variable being undefined or empty so the code would look to bash like something like this:
```
if [ == 'y' ]
```
This is fixed by quoting the variable, but the problem actually comes from the read statement before.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by spbach1234 on 2015-07-14
> **papibe said:**
> Hi spbach1234.

'read' is not done correctly. There should be no '$' preceding the variable name:
```

read -p "Would you like to turn it on? Press Y" **[COLOR=#FF0000]$[/COLOR]**istrue
                                                ^
```
Then the error:
```
[: ==: unary operator expected
```
comes from the 'istrue' variable being undefined or empty so the code would look to bash like something like this:
```
if [ == 'y' ]
```
This is fixed by quoting the variable, but the problem actually comes from the read statement before.

Hope it helps. Let us know how it goes.
Regards.
Thanks this worked perfectly :)

---

