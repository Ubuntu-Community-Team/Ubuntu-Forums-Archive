---
title: "Switch user directly ?"
date: 2019-10-31
forum: General Help
---

### Post by bjngchn on 2019-10-31
If I want to switch user, or login as new user, I have to this (normally):

Click switch user, or logout
Then I see a list of user, I click on one of them, enter pw, and login,
and if I haven't logged out of previous user I can go back with ctrl-alt-f7/f8..
..........
Problem is:

Laptop's own monitor is  not working, and I use external monitor, and
it delays everything by one  input. And when I logout, I see a dark screen, because
there is no previous screen.  I can't choose a user..

How can I switch user directly, such as by using command line, with or
without loggin out at current user?

Everything has a command line version. So must this one. 

.............
Or there can be a solution like this:

Make external monitor act like actual  monitor even before I login as a user.
Is there a way to do this?
............

---

### Post by Skaperen on 2019-10-31
which version of Ubuntu are you using?  for example, i am using Xubuntu 18.04 (Bionic Beaver) LTS (Long Term Support).

i switch users a lot, probably hundreds of times a day, the command "[FONT=courier new]**[COLOR=#0000cd]dm-tool switch-to-user[/COLOR] [COLOR=#a52a2a]username[/COLOR]**[/FONT]" can do this for you.  i even have that set up as keyboard shortcuts under Xfce.  for example Alt+f switches to user "forums" where i read Ubuntu Forums many times a day and am typing this in right now.  Alt+a switches to user "admin".  i have about 16 of these set up because i have so many usernames.

---

### Post by bjngchn on 2019-10-31
Thanks.  I think it is  14.04  I will give it a try.

---

### Post by Skaperen on 2019-10-31
type this command to see your version of Ubuntu:  [COLOR=#0000cd][FONT=courier new]**cat /etc/lsb-release**[/FONT][/COLOR]

---

### Post by bjngchn on 2019-10-31
I used that command and got a dark screen. Then  I had to  turn the laptop off by force. 
 ....... 
Source of the problem is this: laptop's own  monitor doesn't work, 
and external monitor has a one input delay, which makes it dark,
before I type encryption and user pw's, because there is no previous screen in those cases. 


Also when typing encryption pw, I don't see anything,  but just typing the encryption pw works, 
because I don't have to move cursor over something and click with mouse to be ready to type pw. 
But since there are many  users, darkness is a problem  when logging in as a user, or switching user 
(at the first user login  I can handle it, because I login automatically).

.....
So to logout  as user1, and login as user 2, I first allow automatic login as user2, and then shut down,
and restart the computer, enter encryption pw, ..and I also need to set  the next  automatic login user. 
.....
I'm trying to get the same result without changing the user which logins automatically, and without having to
shutdown and restart the computer.

---

### Post by bjngchn on 2019-10-31
Yes, 14.04 LTS.

---

### Post by Skaperen on 2019-10-31
i really don't understand how you have a monitor that "delays everything by one  input".  if you do a do-nothing input, will you then see the results of the previous input?  or does it need to have a change of screen content to update?

it has been many years since i used 14.04.  i updated to 16.04 in June 2016.  i cannot recall what i had working back then.  if [COLOR=#0000cd][FONT=courier new]**dm-tool**[/FONT][/COLOR] works, then that is great.  it is operated by **lightdm** which leaves users logged in.  that means you can switch back to where you left off.  i did set up letting me switch users without password back then (still requires password to login via remote like in ssh),  whatever you can program that runs that command to switch user, i hope that helps.  you might want to make a script to run it.  i did, and called it "[COLOR=#0000cd][FONT=courier new]**stu**[/FONT][/COLOR]".

---

### Post by Skaperen on 2019-10-31
i hope you get a new laptop soon.  Ubuntu 20.04 will be released in 6 months.  maybe you can aim to get one then.

---

### Post by HermanAB on 2019-10-31
Set user command:
$ man su

---

### Post by bjngchn on 2019-10-31
Delay one input:  It means I type 10 characters, I see the first 9 of them.  Also parts of the screen change depending on what I do, but not all parts which were supposed to change.  ...... I'm happy with current version.  ...... I would certainly buy a new laptop, and I would buy 10 more of the current laptop if I can find one (I mean 10). New laptops don't have removable battery, and this means I'm surrendering to  technology instead of controlling it.  This is a war against people sold under the name of convenience. It happens all the time.

---

### Post by ajgreeny on 2019-10-31
Most importantly, 14.04 is now out of support so you should update or clean install to a fully supported version; I recommend 18.04 which, if using Ubuntu, has support until 2023, or if using one of the other DE versions, 2021.

There have beem no application or security updates to 14.04 since April this year so you are vulnerable to malware and other problems if you remain using it.

---

