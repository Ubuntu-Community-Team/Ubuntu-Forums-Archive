---
title: "Flock not working with Hardy Heron"
date: 2008-04-26
forum: General Help
---

### Post by chezzo on 2008-04-26
I've just updated to Ubuntu 8.04 and Flock has stopped working. I have re-downloaded the program and installed it exactly as the guide at [http://www.flock.com/faq/show/30#q_9069](http://www.flock.com/faq/show/30#q_9069) says
When I click on the shortcut I have created, I get the message "There was an error launching the application. Details: Failed to change to directory '$HOME/flock' (No such file or directory)." If I run the command /home/myusername/flock/flock in the terminal, I get "/home/myusername/flock/flock-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory"

Help?!

---

### Post by chezzo on 2008-04-26
i fixed it by installing the debian from getdeb.net, which installed the required libstdc++.so.5
weird though

---

