---
title: "dd: failed to open '/test.file': No such file or directory"
date: 2016-03-04
forum: General Help
---

### Post by ian105 on 2016-03-04
After creating a 50MB test file with dd if=/dev/zero of=test.file bs=1024 count=50000, then attempting to do the following command:

while true
do 
dd if=/test.file of=test2.file bs=1024
rm test2.file
done

...I am getting a scrolling

dd: failed to open '/test.file': No such file or directory
rm: cannot remove 'test2.file': No such file or directory

I have run it after using sudo -i and that doesn't seem to do anything

---

### Post by sudodus on 2016-03-04
Welcome to the Ubuntu Forums :-)

First a warning: ***dd*** is a very powerful tool, but it is also dangerous. It is often nick-named 'disk destroyer'. ***dd*** does what you tell it to do. If you tell it (by mistake) to wipe the family pictures, it will do that without any questions. So please ***double check and triple check*** every single character in the command line with ***dd***.

-o-

If dd finished correctly, it created the file **test.file** in the current directory. You are trying to read the file **/test.file**, which would be located in the root directory '/'. But I suppose that your current directory was another one, maybe your home directory.

What are you trying to do (beyond the coding)? Why the infinite while loop?

If you tell us what you try to do, it will be easier to give relevant help.

---

### Post by yetimon_64 on 2016-03-04
When you open the terminal it automatically opens in your home folder. That is most likely where you made the first test file "test.file" especially since you did NOT use sudo. 

Yet you try to run the commands you list above as "/test.file", which is on root. Add a "~" symbol to the dd commands and paths and it should work. 
```
[FONT=Times]while true[/FONT]
[FONT=Times]do [/FONT]
[FONT=Times]dd if=**~**/test.file of=**~**/test2.file bs=1024
rm **~**/test2.file[/FONT]
[FONT=Times]done[/FONT]
```The "~" symbol is a system variable for your home folder location. The tilde symbol "~" in the paths to the test files above will keep everything in your home folder and should have it work.

Edit: take note of sudodus' warning regarding using dd. Very true it is a powerful tool and can be destructive.

---

### Post by ian105 on 2016-03-04
Thank you both very much. Your suggestions worked. I was doing an assignment that wasn't doing what it was supposed to be doing and it was unnerving. I amusing a Virtual Machine so I shouldn't destroy anything but thank you for the advice.

---

### Post by erick14 on 2016-03-04
Good afternoon, 
  I have the same assignment as Ian, and saw this thread....when I add the tilde as suggested above (glad his worked);
  I am still getting the "dd: failed to open...rm:cannot remove..." scrolling and not doing what it should.

when I do the "ls -l" command, 
  I see in "root@CS340-VirtualBox:/stripefs#" showing the originally created 50MB "test.file"

  I have also created that same 50MB test.file in "root@CS340-VirtualBox:/#" to see if getting that same scrolling
  when attempting to create a I/O load on the VB system.
  - yep, same error

what am I doing incorrectly?

---

### Post by QIII on 2016-03-04
When does your instructor want the assignment to be turned in?

---

### Post by yetimon_64 on 2016-03-04
> **erick14 said:**
> ...what am I doing incorrectly?

You could try doing the whole thing as your normal user; not using the root prompt. May be worth a shot recreating the test file as your normal user and using the code box above keeping everything in your home directory and not mixing it in with that of root. 

Take heed of previous warnings in this thread regarding use of the "dd" command if using it more generally than just a test file example.

---

