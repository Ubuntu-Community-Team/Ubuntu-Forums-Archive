---
title: "proper shebang to run a php script as a file from the terminal"
date: 2015-04-29
forum: General Help
---

### Post by Raner on 2015-04-29
I am trying to get a php script to execute when I run it from the terminal. The scripts name is myscript.php. 

   
  The content of the script is only:

  ```
#!/usr/bin/php

  <?php
  echo ‘it works’;

  ?>

```   
  At the top of the script I use the #!/usr/bin/php shebang.
   
  But when I run the script by going to its directory and using the command
   
  ```
./myscript.php


```   
  I am given the error:
   
  ```
bash: ./myscript.php: /usr/bin/php^M: bad interpreter: No such file or directory


```   
If I just use

```
myscript.php
```

I am told that the command does not exist.


  I have checked /usr/bin for the existence of a php binary and there is one there. There is also a php5 binary. I also the location of the php5 binary in the shebang ( #!/usr/bin/php5 ) and it also does not work.

   
  using just:
```
php myscript.php
``` 
does work.

   
  I am fairly new to linux so I am not sure why this is failing. Any help would be appreciated. (My ultimate aim is to have a cron job setup to run a php script.)

---

### Post by btindie on 2015-04-29
That'll be because you're using DOS style line endings instead of UNIX style. DOS/Windows uses the characters CR+LF to indicated the end of the line while Linux at al only use LF. So bash is seeing the 'CR' character as an additional one in the php filename.

Depending on what you're using to edit the file in it may let you use the correct line ending.

Otherwise if you install the dos2unix package and then run 'unix2dos myscript.php' you'll be able to run your script.

---

### Post by SeijiSensei on 2015-04-29
Use an editor native to Ubuntu to write scripts.  Most systems ship with gedit, though Kubuntu includes the KDE editor kate.  You can also use the nano editor from the command prompt, or something like vi or emacs.

---

### Post by dragonfly41 on 2015-04-29
Remember to make the script executable.

---

### Post by Raner on 2015-04-29
Thanks, I will try these solutions.

---

