---
title: "How do I make a script to automate a task that requires signing into an account?"
date: 2020-04-11
forum: General Help
---

### Post by ash22 on 2020-04-11
I'm using the NordVPN's terminal program to connect to their servers and to do that, I need to enter the program commands in the terminal every time. I made it automatically connect on autostart, but it can sign me out of my account after restarting which means it doesn't connect me unless I use the terminal again. (If I give the command to connect, it will prompt me to sign in.) I want to write a script that automatically signs me in and then connect to my chosen server. How can I script commands that prompts usernames and passwords?

---

### Post by sisco311 on 2020-04-11
Never used it, but I think you can do it with `expect'. 

But I would expect that there is a more secure way to accomplish it.

---

### Post by TheFu on 2020-04-11
Seems like a systemd-unit file with a restart would be better.  if the VPN uses openvpn, you can place the login credentials inside a file.  That is a setting in the .ovpn config files.

---

