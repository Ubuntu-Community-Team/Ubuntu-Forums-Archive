---
title: "how to view and change document right?"
date: 2008-06-29
forum: General Help
---

### Post by sclsch on 2008-06-29
in the command line :
 I type :
 ls -i tomcat-users.xml  
 response:
 193382 tomcat-users.xml
 
 what this number the meaning?

 Why not is -rw-r--r-- 1 ?
 
 And when I type :
 sudo chmod +w tomcat-users.xml 
 no response.
 then I type:
 vi tomcat-users.xml 
 then type :
 a
 the worning is:
 10: Warning: Changing a readonly file
 
 I am surprised.
 how to view and change document right?

---

### Post by linfidel on 2008-06-29
> **sclsch said:**
> in the command line :
 I type :
 ls -i tomcat-users.xml  
 response:
 193382 tomcat-users.xml
 
 what this number the meaning?

 Why not is -rw-r--r-- 1 ?
 
 And when I type :
 sudo chmod +w tomcat-users.xml 
 no response.
 then I type:
 vi tomcat-users.xml 
 then type :
 a
 the worning is:
 10: Warning: Changing a readonly file
 
 I am surprised.
 how to view and change document right?try "sudo vi tomcat-users.xml".  You may not have permission to modify the file.

---

### Post by sclsch on 2008-06-29
thanks u very much. it works well.

---

