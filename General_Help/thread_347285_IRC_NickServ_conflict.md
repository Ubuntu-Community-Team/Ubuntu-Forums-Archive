---
title: "IRC NickServ conflict"
date: 2007-01-27
forum: General Help
---

### Post by dbbolton on 2007-01-27
i registered nick 'dbbolton' with password 123456 (for this post's sake, i'll use a generic entity) with nickserv on irc.freenode.org - this worked fine for quite awhile.

when i try to log in with that nick :
> dbbolton :Nickname is already in use.my guess is that for some wacky reason, i still have a session on the server. one site i googled said that there is a way to ask nickserv to 'kill' a session with a particular nickname that you have registered.

any thoughts ?

---

### Post by dbbolton on 2007-01-28
...

---

### Post by highneko on 2007-01-28
I found some info using google. Hope it helps. You can maybe check if it's you by using whois.
> If your machine crashed or you get disconnected from the server, you will reconnect with an alternate nickname. When this happens, your nickname might be still used by you. This is a ghost -- a copy of yourself that hasn't timed out yet. The server will still see you connected when you are not, but it will die shortly after. You can still kill the ghost user off IRC.

To do this, use the /msg NickServ ghost [nick] [password] command, where [nick] is your nickname that is ghosted, and [password] is your password. However, the fallback is that your address shown must be in the nick's access list and you must already be identified.

When the user or "ghost" is off IRC, use the /nick [nick] command to regain your nickname. Also note that this is an effective way to kick users who takes your nickname.


---

### Post by dbbolton on 2007-01-28
thanks; i'll give it a go

what's strange, though, is that i haven't been able to sign in as 'dbbolton' on freenode for a couple of weeks now

---

### Post by nix4me on 2007-01-28
Did you let your nick expire?  I think 30 days is all they give you, if you go past that without using it, its up for grabs.

nix4me

---

### Post by dbbolton on 2007-01-28
i definitely didnt go 30 days without using it

---

### Post by dbbolton on 2007-03-27
it's automagically working again.

---

