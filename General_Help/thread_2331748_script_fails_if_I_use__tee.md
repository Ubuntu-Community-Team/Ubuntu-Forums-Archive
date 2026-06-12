---
title: "script fails if I use | tee"
date: 2016-07-25
forum: General Help
---

### Post by korstiaan on 2016-07-25
Hi,

I have a large installation script and this works fine if I start it like ./install.sh.
But if I execute it like ./install.sh | tee output.txt 1 line of this script fails:

```
sudo ~/glassfish4/bin/asadmin --user admin change-admin-password
```

This line won't work if I start the script with the | tee?
Normally the script asks for my old password and the 2 times the new one.
But if I use | tee I immediately get an error:

```
Must specify an admin password (e.g., use the --passwordfile option).Usage: asadmin [asadmin-utility-options] change-admin-password
    [--domain_name <domain_name>] [--domaindir <domaindir>]
    [-?|--help[=<help(default:false)>]] 
Command change-admin-password failed.
```

Any idea how to solve?
I need to see the output and in the meantime log it to a text file.

Korstiaan

---

### Post by SeijiSensei on 2016-07-25
What if you simply pipe the output like this:
```
./install.sh > output.txt
```

---

### Post by korstiaan on 2016-07-25
Same problem. Not good. (But also not usefull because I want to see the results in my terminal)

---

### Post by SeijiSensei on 2016-07-25
Rather than invoking sudo in the script, why not just run the script with sudo?

---

### Post by korstiaan on 2016-07-25
Because I also use non-sudo commands in the script.
Anyway, I tried it without sudo and same negative result.

---

### Post by &amp;KyT$0P# on 2016-07-25
So, if you have a shell script that contains **only** that line (and the same first line starting with #!, if any), does it still reacts poorly to use of [FONT=Courier New]tee[/FONT]?

What happens if you just paste that line into your Terminal and stick [FONT=Courier New]| tee output.txt[/FONT] on the end?

---

### Post by DuckHook on 2016-07-25
*Thread moved to **General Help** as the more appropriate forum.*

Please do not use non-standard fonts in your *CODE* inclusions as it is difficult to read.

---

### Post by korstiaan on 2016-08-01
As soon if I use > or | tee the command fails.

---

### Post by &amp;KyT$0P# on 2016-08-01
So more information is needed about
```
~/glassfish4/bin/asadmin
```

What does it do?
Is it a binary or shell script?

---

### Post by korstiaan on 2016-08-02
It seems to be a short script and at the end it calls:

```
[FONT=courier new][COLOR=#000000][SIZE=3][SIZE=3][SIZE=3]exec "$JAVA" -jar "$AS_INSTALL_LIB/client/appserver-cli.jar" "$@"[/SIZE][/SIZE][/SIZE][/COLOR][/FONT]
```

---

### Post by &amp;KyT$0P# on 2016-08-02
Can you please post the whole script?

---

### Post by Keith_Helms on 2016-08-02
So to sum up, you're using a script that's "interactive" in that it requires you to respond with the admin password in a couple of places and you're piping that script to a command that, according to the man page "read from standard input and write to standard output and files"?

It sounds like tee is interfering with sudo prompting for and receiving the admin password.

Is this a script that you wrote or can at least edit?  If so, I'd try something like this:
* Accept the admin password as a parameter in the script.
adminpwd=$1 (assuming no other parameters are needed)
* Where the sudo command is invoked in the script, change it to use the parameter instead of prompting for it.
echo $adminpwd | sudo -S command

Note:  This is somewhat insecure.  If you don't take steps to prevent it, the command with the admin password will wind up in your command history.

---

### Post by Keith_Helms on 2016-08-02
A slightly more secure variation would be to temporarily put the admin password in a file and then in the script do

cat temppwdfile | sudo -S command

making sure to delete the file afterwards.   You could even add a rm temppwdfile at the end of the script to make sure it got done.

---

