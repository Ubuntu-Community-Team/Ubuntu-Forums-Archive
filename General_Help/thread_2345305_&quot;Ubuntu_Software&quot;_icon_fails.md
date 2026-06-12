---
title: "&quot;Ubuntu Software&quot; icon fails"
date: 2016-12-02
forum: General Help
---

### Post by steve169 on 2016-12-02
Just installed Ubuntu 16.04.1 on my desktop PC and updated it.   When I click the "Ubuntu Software" icon (the orange valise with the "A" on the side) , the window appears for a second, then disappears. It does this consistently.     How can I reinstall Ubuntu Software when I don't have access to Ubuntu Software?    Or is reinstallation not the answer?

---

### Post by RobGoss on 2016-12-02
Are you not able to use the software center? 

Try running the following commands:

Install the latest packages
> sudo apt update

Install system current updates
>  sudo apt upgrade 

Install software center
>  sudo apt install software-center    

After running the following commands reboot your machine and try the software center again

---

### Post by steve169 on 2016-12-04
That did the trick beautifully. Many thanks from this newbie.

---

### Post by RobGoss on 2016-12-04
That's great glad I could help, if you have solved your issue would you mind marking this thread as solved. You can do this by using the **Thread tool **at the top of this post

Have a great day

---

