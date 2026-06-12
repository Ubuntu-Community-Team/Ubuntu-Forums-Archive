---
title: "Efax Error: can't open serial port /dev/ttyS1: Permission denied efax-0.9a: 17:33:54"
date: 2019-03-16
forum: General Help
---

### Post by raleigh3 on 2019-03-16
Efax can not send a fax.   
  ```

Socket running on port 9900     efax-0.9a: 17:33:54 Error: can't open serial port /dev/ttyS1: Permission denied     efax-0.9a: 17:33:54 failed page /home/andy/Documents/UHC_Appeal.pdf.001     efax-0.9a: 17:33:54 finished - unrecoverable error

  
```
I tried most of the suggestions from here.

  [URL="https://askubuntu.com/questions/210177/serial-port-terminal-cannot-open-dev-ttys0-permission-denied"]
Serial port terminal > Cannot open /dev/ttyS0: Permission denied[/URL]

---

### Post by HermanAB on 2019-03-17
Run efax with sg and set the group to dialout.

---

### Post by raleigh3 on 2019-03-17
The solution was to add a DSL filter to my landline.

Without it, there was too much noise which interferes with faxxing.

---

