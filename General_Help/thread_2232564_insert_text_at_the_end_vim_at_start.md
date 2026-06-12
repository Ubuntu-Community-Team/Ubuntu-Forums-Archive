---
title: "insert text at the end vim at start"
date: 2014-07-02
forum: General Help
---

### Post by CkDGTAT on 2014-07-02
Dear all,

How can I insert text at the end vim at start through CLI?

Thank you

---

### Post by ubudog on 2014-07-02
Sorry if I misunderstood your question, but you can press "G" (shift+G) to go to the end of a document, and "A" (shift+A) to skip to the end of a line.

---

### Post by nerdtron on 2014-07-02
Press i on the keyboard and you'll enter "Insert mode". You can now edit like a normal text editor. Then press Esc to go back to "Command Mode".

---

### Post by CkDGTAT on 2014-07-03
sudo vim -c ":start|:set syn=sh"

Allows me to start writting directly. How can I insert text

Thank you

---

### Post by nerdtron on 2014-07-03
May I ask why would you like to accomplish this? If it is for a script or something may be we can find an easier solution?

---

### Post by ubudog on 2014-07-03
If it's for a script and you just want to insert some text, you can use the echo command.

For instance,
```

echo "Some text" >> file.txt

```

would append "Some text" to the file file.txt.

---

