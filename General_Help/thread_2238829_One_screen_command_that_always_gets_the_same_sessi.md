---
title: "One screen command that always gets the same session"
date: 2014-08-10
forum: General Help
---

### Post by quadrplax on 2014-08-10
I'm trying to use screen to manage my Minecraft server, and I want to be able to send commands to it over a web interface (phpseclib). For this I need a reliable way to access the console. I'm trying to use screen, but it isn't always reliable. Sometimes "screen -rd" will not find a session or even find more that one. I've heard you can do things like named screen sessions and stuff, but I can't find any easy documentation for screen. Does anyone know of one command I could always use to either reconnect to a session, or create it if necessary? Also, quick other question, is there any way I can interact with a Minecraft console via a shell script? Thanks.

---

### Post by Lars Noodén on 2014-08-10
If you use -S when first creating your screen session, you can identify it by name later thus ensuring that you are getting the same session.

---

### Post by Lars Noodén on 2014-08-10
You can send text to a running screen session using *stuff*  Here it sends "date" followed by a return, thus running the program "date" in the session "minecraft"

```

screen  -S minecraft -X stuff "date $(echo -ne '\r')"

```

Shell scripts can use that method too to send commands to the minecraft server.

---

### Post by quadrplax on 2014-08-12
This method is not disconnecting other copies of the session, I'm not sure if that is a problem or not, for some reason phpseclib is really hard for me. I managed to get it to write the output of its console, and this is what it gives me:
```

screen -S mc
[?1h=[0m(B[1;24r[H[J[H[Jsay Viewing Console

```
I don't get what the deal is there with all those weird symbols before "say". It didn't do that before, when I used "screen -rd". Also, before it would kick me off my PuTTY session that's in the screen session and now it doesn't, but strangely nothing happens in PuTTY, it looks like the site didn't even try to run a command. Here's the code, don't ask me why it works:
```

if ($_GET['function'] == "viewconsole"){
echo "<br><div id=console>";

$randid=rand(0, 1000000);
$consolemsg=strval($randid);

$ssh->read('quadrplax@quadrplax-laptop:~$');
$ssh->write("screen -S mc\n"); // note the "\n"
$ssh->write("say Viewing Console - ID:".$consolemsg."\n");
$consoleoutput=$ssh->read("say Viewing Console - ID:".$consolemsg);
echo nl2br($consoleoutput);
echo '</div> <script>setTimeout("updatenote()",100);</script>';
}

```
If I add the -d flag now (screen -S mc -d) it gives me this output:
```

screen -Sd mc
There are several suitable screens on:

	18221.mc	(08/12/2014 02:39:31 PM)	(Detached)
	18053.mc	(08/12/2014 02:39:09 PM)	(Detached)
	17980.mc	(08/12/2014 02:37:18 PM)	(Attached)
	17932.mc	(08/12/2014 02:36:16 PM)	(Detached)
	17777.mc	(08/12/2014 02:32:13 PM)	(Attached)
Type "screen [-d] -r [pid.]tty.host" to resume one of them.

quadrplax@quadrplax-laptop:~$ say Viewing Console - ID:250421

```
So it looks like it just creates a new session named "mc" every time. Changing the -d to -rd yields same results. I restarted screen and created it without "-rd" at first, and then ran the console viewer with the -rd and it detached my PuTTY session as I expected, and the output was:
```

screen -S mc -rd
Remove dead screens with 'screen -wipe'.

[?1h=[0m(B[1;24r[H[J[H[Jquadrplax@quadrplax-laptop:~$ 
[Kquadrplax@quadrplax-laptop:~$ say Viewing Console - ID:331053

```
So I got that weird text again, and it's the same as last time. Also not sure why it's telling me about "screen -wipe". Btw, if there's a different terminal multiplexer that would make more sense, or something better than phpseclib (I use shared hosting) then I'd be glad to know.

---

### Post by Lars Noodén on 2014-08-13
> **quadrplax said:**
> Btw, if there's a different terminal multiplexer that would make more sense, or something better than phpseclib (I use shared hosting) then I'd be glad to know.

I used to use screen a fair amount but moved over to tmux a while back.  It seems to be an improvement, apparently things under the hood are in good shape I am told, and and from a user perspective it is not as complicated to use.  

But about screen if, you use -dR when creating a session, it will first try to reattach to an existing session (while detaching others using it).  If the reattach fails, it will create a new session and name it from what was included with the -S option.

```

screen -dR -S mc

```

Note the capital R

---

### Post by quadrplax on 2014-08-13
Oh ok thanks for that little flag, screen does seem confusing but it now  serves my needs. Man phpseclib is so weird though. I don't know where I  should ask about that. I tried Stack Overflow, but that can't be bumped  like forums and it wasn't answered. Well if anyone knows what the deal  is here, why doesn't this code work?
```

$ssh->read('quadrplax@quadrplax-laptop:~$');
$ssh->write("screen -dR -S mc\n");
$ssh->write("stop\n");

```
Yes, I do have all the necessary stuff at the beginning of the code. This does work:
```

echo "<br><div id=console>";

$randid=rand(0, 1000000);
$consolemsg=strval($randid);

$ssh->read('quadrplax@quadrplax-laptop:~$');
$ssh->write("screen -dR -S mc\n"); // note the "\n"
$ssh->write("say Viewing Console - ID:".$consolemsg."\n");
$consoleoutput=$ssh->read("say Viewing Console - ID:".$consolemsg);
echo nl2br($consoleoutput);
echo '</div> <script>setTimeout("updatenote()",100);</script>';

```
I don't get why it will write that say command fine yet not the stop one...

As for this thread, I'll mark it as solved since title's problem is.

EDIT: commenting out the following lines:
```

$consoleoutput=$ssh->read("say Viewing Console - ID:".$consolemsg);
echo nl2br($consoleoutput);

```

Makes the screen session never even be taken from me, let alone have the command be executed. It looks like, for some reason, it wants to end in a read command.

EDIT2: Ok, got it to work in a hack-y way, I just test for the prompt after giving it 10 seconds to stop. Why on earth would it need to end in a read...

---

### Post by Lars Noodén on 2014-08-15
> **quadrplax said:**
> Man phpseclib is so weird though. I don't know where I  should ask about that.

There's a [programming talk](http://ubuntuforums.org/forumdisplay.php?f=39) subforum.  They can probablyh answer [PHP](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/) questions.

---

