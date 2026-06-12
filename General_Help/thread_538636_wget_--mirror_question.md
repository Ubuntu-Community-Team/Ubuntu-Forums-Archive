---
title: "wget --mirror question?"
date: 2007-08-30
forum: General Help
---

### Post by Hopeless on 2007-08-30
Hi,

I was doing a --mirror on a web site unfortunatly it (more like me) was not working well...

my .wgetrc file:

```
robots = off
randomwait = on
reject =  *CAT_ID=2,*CAT_ID=12,*FORUM_ID=11,*FORUM_ID=34,*FORUM_ID=44,*FORUM_ID=51,*FORUM_ID=53,*FORUM_ID=5,*FORUM_ID=57,*FORUM_ID=6,*FORUM_ID=7,button_logout.gif,catbg.gif,fishtank.swf,footerback.gif,headbg.gif,headerback.gif,icon_bar.gif,icon_blank.gif,icon_folder_closed_topic.gif,icon_folder.gif,icon_folder_hot.gif,icon_folder_locked2.gif,icon_folder_locked_f.gif,icon_folder_new.gif,icon_folder_new_topic2.gif,icon_folder_new_topic.gif,icon_folder_open.gif,icon_folder_open_topic.gif,icon_folder_sticky.gif,icon_folder_sticky_locked.gif,icon_go_up.gif,icon_group.gif,icon_lastpost.gif,icon_mi_10.gif,icon_mi_11.gif,icon_mi_13.gif,icon_mi_14.gif,icon_mi_1.gif,icon_mi_2.gif,icon_mi_4.gif,icon_mi_6.gif,icon_mi_7.gif,icon_mi_8.gif,icon_mi_9.gif,icon_minus.gif,icon_navmenu_guestbook.gif,icon_navmenu_help.gif,icon_navmenu_home.gif,icon_navmenu_member.gif,icon_navmenu_news.gif,icon_navmenu_search.gif,icon_navmenu_url.gif,icon_pencil.gif
accept = topic.asp*,forum.asp*,forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=* -A gif,jpg,pdf
load_cookies = ~/.mozilla/firefox/xjg5nmlx.default/cookies.txt
limit-rate = 20K 
no_parent = on
convert-links = on
```

the wget:

```
wget --mirror -U Mozilla 'www.website.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage='{1..52}

```
I'm finding many topic.asp files belonging to a reject forum due to a 'next topic >>' link which more or less downloads the whole web site...

when i leave out --mirror it saves all pages in the home directory instead of the [www.website.com/forum/](www.website.com/forum/) directory

So the million dollar question is....how can i download the page:
forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1
and all topic.asp links and pics only to [www.website.com/forum/](www.website.com/forum/) directory?
and the next:
forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=2
topic.asp links etc.....

Many thanks to reading the question !!!!

---

