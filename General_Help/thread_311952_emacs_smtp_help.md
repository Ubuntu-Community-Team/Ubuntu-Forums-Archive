---
title: "emacs smtp help"
date: 2006-12-03
forum: General Help
---

### Post by thomasaaron on 2006-12-03
Hi, folks.

I could use a little help with getting email set up for my emacs.

I want to send mail via my yahoo smtp server.
I've got the pop mail working fine.

When I try to send mail, it connects with yahoo, but authentication fails. 

I've googled and wiki-ed it to death.

Any ideas?

Here is my emacs config file thus far:

[HTML]
(autoload 'vm "vm" "Start VM on your primary inbox." t)
(autoload 'vm-other-frame "vm" "Like `vm' but starts in another frame." t)
(autoload 'vm-visit-folder "vm" "Start VM on an arbitrary folder." t)
(autoload 'vm-visit-virtual-folder "vm" "Visit a VM virtual folder." t)
(autoload 'vm-mode "vm" "Run VM major mode on a buffer" t)
(autoload 'vm-mail "vm" "Send a mail message using VM." t)
(autoload 'vm-submit-bug-report "vm" "Send a bug report about VM." t)


(setq user-full-name "Thomas Aaron"
           mail-from-style 'angles
           user-mail-address "copy@tbaaron.com"
           mail-default-reply-to "copy@tbaaron.com")     
(setq vm-mutable-windows t
           vm-mutable-frames nil)
(setq vm-pop-folder-alist
      '(
        ("pop:pop.mail.yahoo.com:110:pass:MY USERNAME:MY PASSWORD" "work")
      ))


;; Use W3M to read HTML email
(require 'w3m-load)
(setq vm-mime-use-w3-for-text/html nil)
(setq vm-url-browser 'w3m)
(load "w3m")
(setq w3m-input-coding-system 'utf-8
      w3m-output-coding-system 'utf-8)


(setq send-mail-function 'smtpmail-send-it) ; if you use `mail'
(setq message-send-mail-function 'smtpmail-send-it) ; if you use message/Gnus
(setq smtpmail-default-smtp-server "smtp.mail.yahoo.com") ; set before loading library
(setq smtpmail-local-domain "smtp.mail.yahoo.com")
(setq smtpmail-sendto-domain "smtp.mail.yahoo.com")
(setq smtpmail-debug-info t) ; only to debug problems
(setq smtpmail-auth-credentials  ; or use ~/.authinfo
          '(("smtp.mail.yahoo.com" 25 "MY USERNAME" "MY PASSWORD")))






(load-library "smtpmail")

[/HTML]

---

### Post by thomasaaron on 2006-12-04
ahem *BUMP*

---

### Post by pipull on 2007-01-14
I'm having a similar problem, it's something to do with 'Starttls'. It can be installed from the package manager - if you figure it out before me I'd appreciate the answer. :confused:

---

### Post by dcstar on 2007-01-14
> **thomasaaron said:**
> Hi, folks.

I could use a little help with getting email set up for my emacs.

I want to send mail via my yahoo smtp server.
I've got the pop mail working fine.

When I try to send mail, it connects with yahoo, but authentication fails. 
......

If you want to test the actual commands you are trying to send, open up a telnet session and enter the SMTP commands manually, then you can see the actual responses back from the SMTP server.

---

