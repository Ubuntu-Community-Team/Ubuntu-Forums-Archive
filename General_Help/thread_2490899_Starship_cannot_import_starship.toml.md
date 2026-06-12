---
title: "Starship cannot import starship.toml"
date: 2023-09-20
forum: General Help
---

### Post by unknown-entity on 2023-09-20
Whenever I type ```
starship preset tokyo-night -o ~/.config/starship.toml
``` into the terminal, I get the following error:

```
Error writing preset to file: Permission denied (os error 13)
```

I've looked at a bunch of posts detailing a similar error, but none of the solutions have worked for me.
Some guidance would be greatly appreciated

---

### Post by MAFoElffen on 2023-09-20
Can you show the output of these posted within CODE Tags?
```

echo $USER
ls -lah $HOME/.config/starship.toml

```

---

