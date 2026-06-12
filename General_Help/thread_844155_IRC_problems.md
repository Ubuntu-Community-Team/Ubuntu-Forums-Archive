---
title: "IRC problems"
date: 2008-06-29
forum: General Help
---

### Post by AmpersUK on 2008-06-29
How do I log in?

My username is AmpersUK and when I use LISTCHANS I get this error message and am going around in circles.
[INDENT][SIZE=2][COLOR=#204a87](12:05:12) [/COLOR][/SIZE][COLOR=#204a87]**[SIZE=3]AmpersUK:[/SIZE]**[/COLOR][SIZE=3] [/SIZE]
[SIZE=3][COLOR=#909090]listchans[/COLOR][/SIZE]
[COLOR=#cc0000][SIZE=2](12:05:12) [/SIZE]**[SIZE=3]NickServ:[/SIZE]**[/COLOR][SIZE=3] [/SIZE]
[SIZE=3][COLOR=#000000](notice) You are not logged in.[/COLOR][/SIZE]
[/INDENT][SIZE=3][COLOR=#000000]But as far as I am aware, the fact that it shows my User Name means I **must** be logged in?

"Confused" of Tunbridge Wells

[/COLOR][/SIZE]

---

### Post by wrtpeeps on 2008-06-29
Logging in means identifying to nickserv.

It's done differently on various irc servers.

Freenode, OFTC and most others use 

/msg nickserv identify <password>

---

### Post by AmpersUK on 2008-06-29
> **wrtpeeps said:**
> Logging in means identifying to nickserv.

It's done differently on various irc servers.

Freenode, OFTC and most others use 

/msg nickserv identify <password>

I tried this

&#65279;13:05
[COLOR=#cc0000][SIZE=2](13:08:27) [/SIZE]**[SIZE=3]NickServ:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#000000]
(notice) This nickname is registered. Please choose a different nickname, or identify via /msg NickServ identify <password>.[/COLOR][/SIZE]
[COLOR=#cc0000][SIZE=2](13:08:27) [/SIZE]**[SIZE=3]NickServ:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#000000]
(notice) Invalid password for AmpersUK.[/COLOR][/SIZE]
[SIZE=2][COLOR=#204a87](13:08:45) [/COLOR][/SIZE][COLOR=#204a87]**[SIZE=3]AmpersUK:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#909090]
identify xxxxxxxx[/COLOR][/SIZE]
[COLOR=#cc0000][SIZE=2](13:08:45) [/SIZE]**[SIZE=3]NickServ:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#000000]
(notice) xxxxxxxx is not a registered nickname.[/COLOR][/SIZE]

I have replaced my password with xxxxxxxx but somehow it just will not accept ,y password.

Ampers

---

### Post by forger on 2008-06-29
/msg nickserv help register
/msg nickserv register areallycoolpasswordhere [email]myemail@example.com[/email]
> 
14:23:43 [Freenode] -NickServ(NickServ@services.)- ***** NickServ Help *****
14:23:43 [Freenode] -NickServ(NickServ@services.)- Help for REGISTER:
14:23:43 [Freenode] -NickServ(NickServ@services.)-  
14:23:43 [Freenode] -NickServ(NickServ@services.)- This will register your current nickname with NickServ.
14:23:43 [Freenode] -NickServ(NickServ@services.)- This will allow you to assert some form of identity on
14:23:43 [Freenode] -NickServ(NickServ@services.)- the network and to be added to access lists. Furthermore,
14:23:43 [Freenode] -NickServ(NickServ@services.)- NickServ will warn users using your nick without
14:23:43 [Freenode] -NickServ(NickServ@services.)- identifying and allow you to kill ghosts.
14:23:43 [Freenode] -NickServ(NickServ@services.)- The password is a case-sensitive password that you make
14:23:43 [Freenode] -NickServ(NickServ@services.)- up. Please write down or memorize your password! You
14:23:43 [Freenode] -NickServ(NickServ@services.)- will need it later to change settings.
14:23:43 [Freenode] -NickServ(NickServ@services.)-  
14:23:43 [Freenode] -NickServ(NickServ@services.)- You may be required to confirm the email address. To do this,
14:23:43 [Freenode] -NickServ(NickServ@services.)- follow the instructions in the message sent to the email
14:23:43 [Freenode] -NickServ(NickServ@services.)- address.
14:23:43 [Freenode] -NickServ(NickServ@services.)-  
14:23:43 [Freenode] -NickServ(NickServ@services.)- Syntax: REGISTER <password> <email-address>
14:23:43 [Freenode] -NickServ(NickServ@services.)-  
14:23:43 [Freenode] -NickServ(NickServ@services.)- Examples:
14:23:43 [Freenode] -NickServ(NickServ@services.)-     /msg NickServ REGISTER bar [email]foo@bar.com[/email]
14:23:43 [Freenode] -NickServ(NickServ@services.)- ***** End of Help *****


---

### Post by AmpersUK on 2008-06-29
> **forger said:**
> /msg nickserv help register
/msg nickserv register areallycoolpasswordhere [EMAIL="myemail@example.com"]myemail@example.com[/EMAIL]

I tried

[SIZE=2][COLOR=#204a87](13:46:46) [/COLOR][/SIZE][COLOR=#204a87]**[SIZE=3]AmpersUK:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#909090]
register xxxxxxxx [EMAIL="ampers@gmail.com"]ampers@gmail.com[/EMAIL][/COLOR][/SIZE]
[COLOR=#cc0000][SIZE=2](13:46:47) [/SIZE]**[SIZE=3]NickServ:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#000000]
(notice) AmpersUK is already registered.[/COLOR][/SIZE]

And received this message. 

My password is typed in exactly as it always is here. I have been in before OK.

Ampers

---

### Post by forger on 2008-06-29
Let's try again.
The network is Freenode right?
1) Check your email, I think there's an activation email
2) Disconnect and reconnect from the irc server
3) ```
/msg nickserv identify xxx
```
where xxx is your password

Are you trying to list channels available on the server or check the access your nickname has in channels?
For the first one, do:
> /list
For the latter:
> /msg nickserv listchans

P.S. You might want to edit your email in your post here, to avoid spam

---

### Post by AmpersUK on 2008-06-29
> **forger said:**
> Let's try again.
The network is Freenode right?
1) Check your email, I think there's an activation email
2) Disconnect and reconnect from the irc server
3) ```
/msg nickserv identify xxx
```where xxx is your password

P.S. You might want to edit your email in your post here, to avoid spam

When I type /list I get a window opened with a lot of chanels and I enclose a screenshot.

When I type listchans, I get an error message "You are not logged in".

I have received no email I can find.

identify <password> gets the error message stating: "Invalid Password for AmpersUK"

If I type "LOGOUT" i GET A MESSAGE SAYING i AM NOT LOGGED IN.

---

### Post by AmpersUK on 2008-06-29
> **forger said:**
>  P.S. You might want to edit your email in your post here, to avoid spam

It's a web address, not an email address.

Ampers

---

### Post by forger on 2008-06-29
You might have to enter #freenode and solve this.

> It's a web address, not an email address.
I'm talking about your email in this post: [http://ubuntuforums.org/showpost.php?p=5285027&postcount=5](http://ubuntuforums.org/showpost.php?p=5285027&postcount=5)

---

### Post by AmpersUK on 2008-07-02
> **forger said:**
> I'm talking about your email in this post: [http://ubuntuforums.org/showpost.php?p=5285027&postcount=5](http://ubuntuforums.org/showpost.php?p=5285027&postcount=5)

Ah! I see. Thanks for the warning but I get about a thousand spam emails a month but GMail takes care all of them. I get the odd one roughly every other month but GMail tends to lean very quickly when I mark them as spam.

I feed seven email address through GMail and then have GMail push them through to Evolution.

Ampers

---

