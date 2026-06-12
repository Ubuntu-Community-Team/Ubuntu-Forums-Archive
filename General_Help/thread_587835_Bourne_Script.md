---
title: "Bourne Script"
date: 2007-10-23
forum: General Help
---

### Post by darkblade25 on 2007-10-23
I am new at scripting so bear with me.
I have a bourne script that just which changes to directory to what ever a person enters.
		echo "Enter Directory"
		read newDirectory
		direc=`$newDirectory`
		cd $direc
		pwd

This is not all of it, just part. But when I run this with the newDirectory being /home/I get 
demo_script: 31: /home/: Permission denied
Any clues on how to fix this? The file is chmod to 777

---

### Post by Nunu on 2007-10-23
have you tried adding the sudo command in the script it should prompt you for a password.

---

### Post by bigboy_pdb on 2007-10-23
I think you should change your script to:
```

echo "Enter Directory"
read newDirectory
cd "$newDirectory"
pwd

```

Back quotes are used to redirect screen output to a command. For example, for pwd=`pwd` the variable pwd is now a string that is the working directory because the command "pwd" prints the working directory to the screen. When you used back quotes around the variable, the shell was trying to find a command within the path and execute it.

---

### Post by darkblade25 on 2007-10-23
Thanks it worked bigboy_pdb.

---

