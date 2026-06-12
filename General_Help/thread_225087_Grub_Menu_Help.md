---
title: "Grub Menu Help"
date: 2006-07-29
forum: General Help
---

### Post by Brando569 on 2006-07-29
is there anyway to stop grub from making the recovery option everytime you enter a new kernel into the list? i never use the recovery options (cuz its easy to do it from grub itself if something screws up) and it just annoys me. thanks.

---

### Post by philippe_carlo on 2006-07-29
I'm afraid the scripts that come with the packages are responsible for that. So there is no real way of avoiding this. You could however make small startup script that cleans these entries up.

Here's a start:
```

ctr=0
IFS="
"

for entry in `cat /boot/grub/menu.lst`;
do
  recovery_entry=`echo $entry | grep recovery | grep kernel`
  if [ "$recovery_entry" = "" ];
  then
      if [[ $ctr > 0 && $ctr < 5 ]];
      then  
	  #echo "<-$ctr- $entry"
	  ctr=$((ctr+1))
      else
	  echo "$entry"
      fi
  else
    #echo "<--- $entry"
    ctr=1
  fi
done

```

Not perfect, since it deletes empty lines.

---

### Post by Brando569 on 2006-07-29
cool thanks, ill try it out...

edit:

didnt work for me buddy :( it did remove the boot option for windows, maybe its tryin to tell me something :lol:

---

