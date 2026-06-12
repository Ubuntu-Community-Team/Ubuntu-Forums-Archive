---
title: "traceroute in Edgy"
date: 2006-12-21
forum: General Help
---

### Post by croppyboy on 2006-12-21
Is traceroute not available in Edgy? When I type "traceroute" in the terminal I get the following error:

> bash: traceroute: command not found

I used traceroute in Dapper . . . does anyone know what happened?

---

### Post by Ramses de Norre on 2006-12-21
```
sudo aptitude install traceroute
```

---

### Post by croppyboy on 2006-12-21
Thanks for the help!

I don't remember having to install it in Dapper . . . I thought it was pre-installed . . .

---

### Post by maxamillion on 2006-12-21
It was pre-installed in dapper, it was replaced by the command "tracepath" in edgy (as far as I know)

---

### Post by croppyboy on 2006-12-21
Thanks for the info . . . that's what I thought.

I've never used tracepath. Do you know what the difference is between it and traceroute?

---

