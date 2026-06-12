---
title: "Correct way to edit file"
date: 2020-08-27
forum: General Help
---

### Post by aboka on 2020-08-27
hi, im using Ubuntu 20.04 LTS and would like to ask the correct way to edit a file, especially config file. I am using Nano as the editor, i hv no idea howto add the empty spaces(ident) in front of a line. Should i use Space bar or TAB. When i use TAB, it will have a 'green trail' on the empty spaces. I forget which program, but when i try to put empty spaces in front of a line, it give errors as the program cant read them.

For the eg. below, if we like to add a new line, should we use Space bar or TAB in front?

```

{
    "server":"my_server_ip",
    "server_port":8388,
    "local_port":1080,
    "password":"barfoo!",
    "timeout":600,
    "method":"chacha20-ietf-poly1305"
}[COLOR=inherit][FONT=&amp]}[/FONT][/COLOR]
```

thank you,

---

### Post by Impavidus on 2020-08-27
Usually it doesn't matter (leading whitespace is usually ignored), but sometimes it does (Python code, makefiles). It's best to keep things consistent within a file, even if only because the width of a tab can vary. It's usually set to 4 spaces these days, but if you open the file in an editor set to interpret a tab as 8 spaces and your file freely mixes tabs with series of spaces, the formatting is messed up.

So I suggest you just use what the existing lines use. If they use spaces, just hit space a few times. Some text editors can be configured to insert a number of spaces when you hit tab.

---

### Post by The Cog on 2020-08-27
I agree with Impavidus. If you're editing an existing file then go with whatever standard is already used in that file. Doing otherwise is inviting hard to debug problems. 
If you are starting a new file then I recommend using spaces. Yaml configuration files regard tab characters as invalid.

---

### Post by aboka on 2020-08-27
hi all, thanks for the suggestions - 

1) how do we find out the 'default standard'? how do we know whether its space or tab? especially it has 4 leading spaces, it could be both

thank you,

---

### Post by SeijiSensei on 2020-08-27
On a existing file, just use the cursor. Either it will go along space-by-space, or it will jump to the next tab stop.

---

### Post by ActionParsnip on 2020-08-27
Depends on the standards in your organisation. In netplan, what you use is VERY specific and matters

---

### Post by HermanAB on 2020-08-27
The correct way?  Why? With ed of course!

Ed is the standard UNIX editor:
[https://www.gnu.org/fun/jokes/ed-msg.en.html](https://www.gnu.org/fun/jokes/ed-msg.en.html)

Graphical examples for ed:
[https://www.geeksforgeeks.org/ed-command-in-linux-with-examples/](https://www.geeksforgeeks.org/ed-command-in-linux-with-examples/)

There is even a book on ed:
[https://www.amazon.com/Ed-Mastery-Standard-Unix-Editor-ebook/dp/B07BVBSDNZ](https://www.amazon.com/Ed-Mastery-Standard-Unix-Editor-ebook/dp/B07BVBSDNZ)

and a quick help page to get you going with ed:
[https://wiki.c2.com/?EdIsTheStandardTextEditor](https://wiki.c2.com/?EdIsTheStandardTextEditor)

):P

---

### Post by TheFu on 2020-08-27
> **aboka said:**
> hi all, thanks for the suggestions - 

1) how do we find out the 'default standard'? how do we know whether its space or tab? especially it has 4 leading spaces, it could be both

Experience. 
I think only Makefiles care any more. Unless you modify those, which is highly odd for an end user, it shouldn't matter.

For system files, the safe way to edit is to use **sudoedit**. Any editor you like can be configured.  Nano is a terrible editor for productivity. Anything else would be better, but is you edit 1 file a month, probably not worth changing.  I edit 20+ files a day. A productive editor s extremely important. Abut 99% of the time, I use vim. In the beginning, I used emacs for about 6 months as my vi skills became stronger. Around month 5, I kept switching emacs into vi-mode to get stuff done. Back then, those were the only real editor choices.
If I was starting with Linux today, it would probably be **geany** that I used.
After installing it, add this line to the bottom of your ~/.bashrc file.
```
export EDITOR=geany
```
Logout, login, use **sudoedit** and see that nano isn't used, rather geany is.  This is only needed for system setting, not normal files owned by your userid.

---

### Post by aboka on 2020-08-27
@SeijiSensei thanks and wonder why i never thought of that ;)

@ActionParsnip yeah i think its the netplan thats complaining about those 'whitespace'

@HermanAB thanks but i think i will stick with Nano in the meantime with the tips here

@TheFu i just tried sudoedit, it looks just like Nano. what is their difference? i only use the CLI, so geany not suitable for my case

And lastly, Thanks all for the valuable tips!

p/s - anyone know why i dont receive email notifications? i login with SSO and according to the thread tools, im subscribed since im posting this and it show 'Unsubscribe from this Thread'

---

### Post by HermanAB on 2020-08-27
The very first editor I used on a computer, was actually ed.  

It was actually almost better than working with punch cards...

---

### Post by TheFu on 2020-08-27
> **aboka said:**
>  @TheFu i just tried sudoedit, it looks just like Nano. what is their difference? i only use the CLI, so geany not suitable for my case

And lastly, Thanks all for the valuable tips!

p/s - anyone know why i dont receive email notifications? i login with SSO and according to the thread tools, im subscribed since im posting this and it show 'Unsubscribe from this Thread'

Nano is the default editor. For noobs, it is useful.  For people like me, the 1st thing I do on any new Linux system is *sudo apt purge nano*. This resets all the defaults to a small version of vim, which is my preferred, get things done, editor.  The **EDITOR** environment variable controls which editor sudoedit will use. Actually, it will control the file editor that every program on the system uses. There are a few of these key environment variables that make our systems "feel" customized.

I'd guess that the servers providing the forums here are overloaded. When any Unix server gets overloaded, the first thing to be disabled is email. It is a safety thing and part of sendmail and postfix, probably all other MTAs.  The most reliable way I know to see updated to threads here is to click the "Settings" at the top of any forum page when logged in. 

Nobody commenting here has system admin control over these forums.  Canonical runs the server for the community and they make upgrade/fix decisions mainly based on security needs.

---

### Post by aboka on 2020-08-27
a good news, not relate to the question thou - i got email notifications now after mentioning it here. perhaps the wizard admin here saw me msg and magically makes them notification works :D

'ed' is a cool name for an editor ;)

p/s - TheFu, jus notice your msg after posting this. Got it. And the reason i use Nano is bcoz of its 'simplicity'(altho not very) compare to Vim etc. I choose from few of them when first started to learn Ubuntu, and Nano is the easiest one. For eg. i cant find ways to close or save the file in Vim.... :qa + enter or something?

---

### Post by aboka on 2020-08-27
ok i think i will stick with Nano for now and check the 'default standard' with the arrow keys and follow them. but what if for some 'system file' that are very strict like netplan/system files? any tips on howto handle them?

cheers,

---

### Post by TheFu on 2020-08-27
> **aboka said:**
> ok i think i will stick with Nano for now and check the 'default standard' with the arrow keys and follow them. but what if for some 'system file' that are very strict like netplan/system files? any tips on howto handle them?

Use a better editor, like **geany** or even gedit (Gnome) or kate (KDE)?
Nothing can replace an experienced editor (person). It is about the human using the tool, not the tool alone.  Unix has a very different philosophy than Windows.

---

### Post by aboka on 2020-08-28
ok guys, i think i will give Vim another try as it got 'color code' so its much easier to edit a large file with lotsa nested code.

thanks again and have a nice weekend :)

---

### Post by TheFu on 2020-08-28
Run **vimtutor** from any shell prompt to get a quick how-to.

Learning vim is like learning anything that is flexible and complex. It takes time. Commit to learning one new thing each week after you get passed the first 30-60 days and baby-vim use. It will take years.  

Every key has multiple purposes, but there is a method, an elegance, to the program.  
If you work with columns, visual mode selections will make your year.

You can force bash command editing to use "vi-mode" too, but that's a little too hard-core even for me. ;) The emacs bindings are fine.

---

