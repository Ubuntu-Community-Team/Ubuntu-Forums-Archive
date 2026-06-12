---
title: "Trouble with exim4 in Ubuntu 7.10"
date: 2008-05-01
forum: General Help
---

### Post by Titan8990 on 2008-05-01
Alright, I am trying to set up a mail server. Before I get into IMAP and delivering to other machines I am trying to receive mail locally. My config file looks like this:

dc_eximconfig_configtype='internet'
dc_other_hostnames='{my domain here}'
dc_local_interfaces=''
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='false'
dc_mailname_in_oh='true'
dc_localdelivery='maildir_home'

So I set up evolution to the maildir in my home folder. exim4 delivers mail to the maildir under the folder "cur". I can open the emails and read them in text mode but evolution acts like they are not even there. 

Evolution is set up for maildir format and I have tried using the maildir as well as it's children. I have been messing with this for a while and I am out of ideas. 

Anyone have a clue on why evolution will not pull the mail out of the maildir?

Do I need another MDA such as procmail to move it to the MUA? I was under the impression the exim4 was both a MDA and a MTA.

Any help is appreciated.

I have no issues sending mail using evolution and exim4.

---

