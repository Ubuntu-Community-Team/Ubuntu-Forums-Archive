---
title: "How to access my root folder with admin access?"
date: 2017-04-16
forum: General Help
---

### Post by uzumakifahim on 2017-04-16
I've installed apache folder on Ubuntu 16.04. Now I want to access  with admin access frequently. Till now I've used following command :
  ```
gksu nautilus

```  Since few days ago. It's not working at both of my PC. It's giving me the message that 
  [HTML]   Permission Denied

 [/HTML]  It's really annoying. I want to access the root folder within GUI just like before. How can I do that? Please help.

---

### Post by howefield on 2017-04-16
Does..

```
sudo -H nautilus
```

work ?

---

### Post by uzumakifahim on 2017-04-17
Thanks this solution is working perfectly. Regards.

---

### Post by howefield on 2017-04-17
> **uzumakifahim said:**
> Thanks this solution is working perfectly. Regards.

Cool, you're welcome and thanks for marking the thread as solved.

---

