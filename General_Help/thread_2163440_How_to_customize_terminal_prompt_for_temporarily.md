---
title: "How to customize terminal prompt for temporarily"
date: 2013-07-18
forum: General Help
---

### Post by dmahesh22 on 2013-07-18
When we open terminal by default we get 'username@username-descktop' as terminal prompt and  gets changes as we switch to other folders.Is there any approach to customize this for temporarily as we are able to customize terminal title. 

Thanks

---

### Post by DeathByDenim on 2013-07-18
You can change the environment variable **PS1**. If you type
```
echo $PS1
```
then you'll see what it is now. It contains lots of cryptic codes, but they are explained here for example: [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)
So if you type:
 ```
export PS1="\u $ "
```
then you'll just get 'username $ ' as your prompt. Have fun! :)

---

### Post by dmahesh22 on 2013-07-18
Thanks,hope above will be for temporary only ?

---

### Post by cool110 on 2013-07-18
Environment variables set with export will remain until the terminal window is closed, permanent changes require editing ~/.bashrc

---

### Post by steeldriver on 2013-07-18
Here's a nice simple option I discovered recently if you're just looking to temporarily limit the length of the prompt, for example if you're nested so deep that the standard prompt is filling the whole width of the terminal

```
export PROMPT_DIRTRIM=2
```

will immediately limit the number of directories in the path portion of the prompt to 2 and so on. You can revert it with

```
unset PROMPT_DIRTRIM
```

---

