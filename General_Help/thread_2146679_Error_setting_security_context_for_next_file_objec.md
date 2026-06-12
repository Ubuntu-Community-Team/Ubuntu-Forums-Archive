---
title: "Error setting security context for next file object"
date: 2013-05-19
forum: General Help
---

### Post by Ironner on 2013-05-19
Hi to all,
I have this error when I try to install any packages:
sudo apt-get install vim-tiny 
sudo: unable to resolve host pcdigg
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Pacchetti suggeriti:
  indent
I seguenti pacchetti NUOVI saranno installati:
  vim-tiny
0 aggiornati, 1 installati, 0 da rimuovere e 53 non aggiornati.
È necessario scaricare 0 B/411 kB di archivi.
Dopo quest'operazione, verranno occupati 846 kB di spazio su disco.
Selecting previously unselected package vim-tiny.
(Lettura del database... 270949 file e directory attualmente installati.)
Estrazione di vim-tiny (da .../vim-tiny_2%3a7.3.429-2ubuntu2.1_amd64.deb)...
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
[COLOR=#b22222]Error setting security context for next file object:: Operation not supported[/COLOR]
Configurazione di vim-tiny (2:7.3.429-2ubuntu2.1)...
update-alternatives: viene usato /usr/bin/vim.tiny per fornire /usr/bin/rview (rview) in modalità automatica.
update-alternatives: viene usato /usr/bin/vim.tiny per fornire /usr/bin/vi (vi) in modalità automatica.
update-alternatives: viene usato /usr/bin/vim.tiny per fornire /usr/bin/view (view) in modalità automatica.
update-alternatives: viene usato /usr/bin/vim.tiny per fornire /usr/bin/ex (ex) in modalità automatica.

Anyone know what is this?

---

### Post by 2F4U on 2013-05-19
Am I right in assuming that pcdigg is the hostname of your machine? If yes, can you post the content of /etc/hosts?

---

### Post by Ironner on 2013-05-19
> **2F4U said:**
> Am I right in assuming that pcdigg is the hostname of your machine? If yes, can you post the content of /etc/hosts?

Hi [COLOR=#000000]2F4U thank you, I fixed the problem of "[/COLOR][COLOR=#000000]sudo: unable to resolve host pcdigg" but not the errors "[/COLOR][COLOR=#B22222]Error setting security context for next file object:: Operation not supported[/COLOR][COLOR=#000000]" [/COLOR]:(

---

### Post by Ironner on 2013-05-20
I think the problem is reiserfs + selinux, but I receive an error when I unintall it. Do you know how uninstall it?

---

