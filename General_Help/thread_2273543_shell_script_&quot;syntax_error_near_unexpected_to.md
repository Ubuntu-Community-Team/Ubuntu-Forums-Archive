---
title: "shell script &quot;syntax error near unexpected token `fi' &quot;"
date: 2015-04-13
forum: General Help
---

### Post by anon9815 on 2015-04-13
I have been trying to write a script to verify the integrity of backed up files but have run in to a problem  it gives syntax error near unexpected token `fi' and its not obvious why  could someone  advise me on what i am doing wrong/how i should do it ?   contents of script      ```
 #!/bin/bash  user=`id|cut -f 2 -d \(|cut -f 1 -d \)`  size=`du -s /home/$user/results 2>/dev/null |cut -f 1` zero=`du -s /proc/ 2>/dev/null |cut -f 1` echo 'which drive ?'  read drive  cd /media/$user/$drive  if jacksum -c Checksums/$drive/files\ checksums|tee /home/$user/temp && grep -v -E ^\\[OK\] /home/$user/temp |grep ^\\[  > /home/$user/results  fi  if [ $size > $zero ];  then  cat /home/$user/results |mail $user  else echo 'All files ok'  fi 
```

---

### Post by Keith_Helms on 2015-04-14
It looks like the following if statement is missing "; then *commands*" before the terminating fi token. 

```
if
jacksum -c Checksums/$drive/files/checksums|tee /home/$user/temp && grep -v -E ^\\[OK\] /home/$user/temp |grep ^\\[  > /home/$user/results
fi
```

---

