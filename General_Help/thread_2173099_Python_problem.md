---
title: "Python problem"
date: 2013-09-08
forum: General Help
---

### Post by blackout2 on 2013-09-08
I'm not sure where to post this, move it if you have to, but I have been trying to figure this out by myself, and I have finally broke down, and come here for help.
Here is the code:

```

#!/usr/bin/python
user=raw_input("Enter Username: ");
print "Hello, " + user;


passw=raw_input("Enter password: ")


openf = open('pass');


find1 = openf.readline();
find2 = openf.readline();
find3 = openf.readline();
find4 = openf.readline();




array = []


array.append("4")
array.append("5")
array.append("6")
array.append("7")


array[0] = find1
array[1] = find2
array[2] = find3
array[3] = find4


password1 = array[0]
password2 = array[1]
password3 = array[2]
password4 = array[3]


if user == "<UserName>" and   password1 == passw:
    print "You have been granted access"
elif user == "<UserName>" and password2 == passw:
    print "You have been granted access"
elif user == "<UserName>" and password3 == passw:
    print "You have been granted access"
elif user =="<UserName>" and password4 == passw:
    print "You have been granted access"
else:
    print "Error"

```

I JUST started using  Python, and I have been using Bash, but I needed this in Python, so I looked at some documentation, and came up with this. It's probably really inefficient, but I don't care, I just want to get it done. What happens is, array[], doesn't seem to want to be used in the if statement, I think it has to do with the if, because if I do ```
 print password1 
``` then I get my password from the file, but it doesn't work in the If statement. Please help as soon as you can.

---

### Post by Vaphell on 2013-09-08
what do you mean array[] doesn't work in if statement? It most certainly does.
```
$ python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:04:36) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> user='user'
>>> passw='ccc'
>>> array=[ '4', '5', '6', '7' ]
>>> array
['4', '5', '6', '7']
>>> array[0]='aaa'
>>> array[1]='bbb'
>>> array[2]='ccc'
>>> array[3]='ddd'
>>> array
['aaa', 'bbb', 'ccc', 'ddd']
>>> if   user == 'user' and array[0] == passw: print 'true a[0]'
... elif user == 'user' and array[1] == passw: print 'true a[1]'
... elif user == 'user' and array[2] == passw: print 'true a[2]'
... elif user == 'user' and array[3] == passw: print 'true a[3]'
... else:                                      print 'fail'
... 
true a[2]
```
what happens exactly?


in case you want 1 username tested against 4 different passwords you could test it with **user == 'user' and passw in array**, but your code doesn't make it clear

---

### Post by blackout2 on 2013-09-08
My code takes 4 variables, and stores a line(password) in each variable. The array stores all 4 of those passes, it is then supposed to check a single username against all 4. I have more"users" to add in the future, but this is just the first part. Once I figure this out,  the rest will follow. I think I know why my problem happens. If I do [code]print array[0]#orprint password1[\code]They both output the password, because the variable is being called, and thus, openf.readline() executes. However, when I use the variable in the if statement, the variable isn"t being used. I need to get 'find' to be called, in the if statement, do you get me?

---

### Post by Vaphell on 2013-09-08
one word: newline

```
#!/usr/bin/env python

user = raw_input( "Enter Username: " )
print "Hello, " + user

passw = raw_input( "Enter password: " )

array = [ [COLOR="#0000FF"]line.strip()[/COLOR] for line in open('pass') ]
array_test = [ [COLOR="#FF0000"]line[/COLOR] for line in open('pass') ]  # this is equivalent to what you have

[B]print [COLOR="#0000FF"]array[/COLOR], [COLOR="#FF0000"]array_test[/COLOR], "passw='%s'" % ( passw ) # debug print
[/B]

if user == "user" and passw in array:
	print "You have been granted access"
else:
	print "Error"
```

```
$ ./users.py 
Enter Username: user
Hello, user
Enter password: ccc
**['aaa', 'bbb', [COLOR="#0000FF"]'ccc'[/COLOR], 'ddd'] ['aaa[COLOR="#FF0000"]\n[/COLOR]', 'bbb[COLOR="#FF0000"]\n[/COLOR]', [COLOR="#FF0000"]'ccc\n'[/COLOR], 'ddd[COLOR="#FF0000"]\n[/COLOR]'] passw='ccc'**
You have been granted access
```

---

### Post by blackout2 on 2013-09-08
Thanks, that looks like it will work. Looks like this can be marked [SOLVED]....
I though it had something to do w/ new line, but I wasn't sure how to get rid of it, thank you.

---

### Post by blackout2 on 2013-09-08
I had to re-format some of it, and make it my own, but is works now, thanks.

---

