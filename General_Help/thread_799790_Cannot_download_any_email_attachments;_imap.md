---
title: "Cannot download any email attachments; imap"
date: 2008-05-19
forum: General Help
---

### Post by yngvi on 2008-05-19
Hi all,

the situation:
I can not download any email attachments (of a size greater than say 100k) from our company imap server. It doesn't matter which email client I use (usually thunderbird). Thunderbird just tells me "Downloading message..." but never stops downloading. The attachment I try to save on disk always has a size of 0k. 

Email reception and sending (without attachments) works perfectly though.

Using exactly the same email configurations in windows/thunderbird works just fine, hence all these funky advanced options in thunderbird are not an issue here.

It seems that my Ubuntu (hardy) system is somehow blocking the download of those attachments.

The firewall seems to be off, or rather permitting everything:
```
iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Are there any other scripts/files etc which I could check that might be causing this problem?

A log of thunderbird when starting the download of an attachment gives:
```
1129732432[1787e90]: ReadNextLine [stream=17acad0 nb=39 needmore=0]
1129732432[1787e90]: 1786d60:mail2:S-INBOX:CreateNewLineFromSocket: * 32 FETCH (UID 1271 BODY[2] {144296}

1129732432[1787e90]: ReadNextLine [stream=17acad0 nb=78 needmore=0]
1129732432[1787e90]: 1786d60:mail2:S-INBOX:CreateNewLineFromSocket: JVBERi0xLjQNJeLjz9MNCjQ3IDAgb2JqIDw8L0xpbmVhcml6ZWQgMS9MIDEwNTQ0Ni9PIDQ5L0Ug
```

and then repeating the last line (though with different characters and numbers) forever and ever.

Any help is greatly appreciated.

---

