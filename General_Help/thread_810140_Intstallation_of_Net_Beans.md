---
title: "Intstallation of Net Beans"
date: 2008-05-28
forum: General Help
---

### Post by pauldr on 2008-05-28
I am very new to Ubuntu and linux, but enjoy it so far.  I am trying to install Net Beans and receive the following error:

Could not open the file /home/paul/Desktop/netbeans-6.1-linux.sh.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I tried following the installation instructions from sun.com which state:


   1. Navigate to the directory that contains the installer.

   2. If necessary, change the installer file's permissions to make the binary executable by typing from a command prompt:

          $ chmod +x your_binary_executable

      Note: Be sure to replace your_binary_executable with the actual filename of the binary that you downloaded.

   3. Launch the installer by typing from a command prompt:

          $ ./your_binary_executable

      Note: Again, be sure to replace your_binary_executable
      with the actual filename of the binary that you downloaded.

I receive an error stating that the command not found.

I am lost, can anyone help?

Paul

---

### Post by pointone on 2008-05-28
Try running: 

```
chmod +x /home/paul/Desktop/netbeans-6.1-linux.sh
/home/paul/Desktop/netbeans-6.1-linux.sh
```

Does this raise the same error?

Try downloading your file(s) again; it could possibly be a corrupt download.

---

