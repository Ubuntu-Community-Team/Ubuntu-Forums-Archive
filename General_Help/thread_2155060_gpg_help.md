---
title: "gpg help"
date: 2013-06-16
forum: General Help
---

### Post by royaceArnold on 2013-06-16
I have(GnuPG) 1.4.10 and when I enter gpg from command line the screen displays
gpg: Go ahead and type your message ...
I can input text but I do not know how to terminate the keyboard input and save the the text in a file. The only way I can get out of the text input mode is to type a Ctrl C. Then the screen shows the command line. I have studied help files and info files for "gpg" and can find no help. Does anyone know how to save and exit out of "gpg" when entered with no argument or file given just (gpg) and nothing else. Please help if anyone knows about this.

---

### Post by agillator on 2013-06-17
Check the man page for specifics. You need the --encrypt command and the --output option. So, the command will be something like 'gpg --encrypt --output encrypted-file'. It will ask you for the recipient's id to look up the public key, then will accept input from the keyboard. If finally entering a blank line does not end the program, use Ctl-D which means end-of-file. The encrypted file will then be in the file 'encrypted-file'.  Added: The problem with using just the 'gpg' command is that it doesn't really know what to do or who to encrypt the input for. I don't know why the program acts as it does.

---

### Post by Lars Noodén on 2013-06-17
When you are editing text as input you can use ctrl-d on a blank line to exit.  It works in many other situations, too.  Just be careful not to do it twice in a row, becaue the first one will exit from gpg and the second one will exit from bash.

---

### Post by sudodus on 2013-06-17
Welcome to the Ubuntu Forums :-)

Look at this link, I think it will answer some of your questions
[URL="http://ubuntuforums.org/showthread.php?t=2121512"]
how to encrypt message (not file) in terminal?[/URL]

---

### Post by coffeecat on 2013-06-18
Not a tutorial.

*Thread moved to **General Help**.*

---

