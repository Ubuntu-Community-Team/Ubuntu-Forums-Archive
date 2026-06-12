---
title: "how to change sudo timeout properly?"
date: 2021-03-24
forum: General Help
---

### Post by lenny444 on 2021-03-24
hi

how do you change the sudo timeout?

i have found serveral ways 4 to be exact?

1. cd /etc/sudoers.d
2. sudo visudo -f my_username
3. add line
Defaults timestamp_timeout=1

am i right that =1 is 1 minute?
is =0 ask for password everytime (this is what i am looking for the most secure option)

2. 

1. sudo visudo
2. add line
Defaults timestamp_timeout=1

3.

1. sudo visudo
2. In the file, you'll want to add at the end:
Defaults:my_username timestamp_timeout=1

4.

1. sudo visudo
2. look for the following line in the sudoers file:

Defaults env_reset

3. Edit the above line by adding timestamp_timeout=x to its end. It should like this:

Defaults env_reset,timestamp_timeout=x

Where x is the timeout value for which it will wait before asking again for the sudo password

then reboot

which is the best option or correct?

have i missed any cmds in the instructions?

thank you

---

### Post by HermanAB on 2021-03-24
I think what you are looking for is passwd_timeout
[https://linux.die.net/man/5/sudoers](https://linux.die.net/man/5/sudoers)

---

