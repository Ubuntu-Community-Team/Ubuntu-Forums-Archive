---
title: "sequence of thunderbird and firefox starting"
date: 2013-01-31
forum: General Help
---

### Post by rnerwein on 2013-01-31
hi
i think there is a little "bug" in combination with firefox and thunderbird starting.
what i did is (it is always reproduceable);)
1. ps -ef | grep firefox --> result is firefox isn't running.
2. starting thunderbird  --> works fine
3. select a new mail in thunderbird --> results in:

Firefox is already running, but is not responding. To open a new window, you 
must first close the existing Firefox process, or restart your system.
(for a newcommer the message "restart your system" is very hard !!!!!)

4. ps -ef | grep firefox results in:
richi     4759     1 45 08:39 ?        00:00:04 /usr/lib/firefox/firefox [http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de]("http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de")
richi     4779     1  3 08:39 ?        00:00:00 /usr/lib/firefox/firefox [http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de](http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de)
richi     4826  4759  3 08:39 ?        00:00:00 /usr/lib/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omn

for a hint: this behavior don't happen when i start "firefox" first and then
thunderbird.
 
5. hi guys - this don't hassle me - but it is a little bug
cheers
  richi

---

### Post by SeijiSensei on 2013-01-31
The "already running" error occurs when firefox was not shut down cleanly.  If you look in $HOME/.mozilla/firefox you'll see a directory named something.default.  Enter that directory and delete any "lock" and ".parentlock" files you see there:

```

cd ~
cd .mozilla/firefox
cd abcdefg.default
rm -f lock .parentlock

```

Replace "abcdefg" with the name of the default directory on your system.

This problem doesn't occur as often as it once did, so Mozilla must have cleaned up some of the code that removes lock files.  But it does still happen as you have discovered, and it must cause novice users fits because the reason for the problem is so obscure.

I think rebooting may clean out the locks, but that's not an acceptable solution on *nix systems where rebooting is always the last resort.

Thunderbird can also fall victim to this problem, but it doesn't happen as often with TBird as it does with Firefox.

---

### Post by rnerwein on 2013-01-31
> **SeijiSensei said:**
> The "already running" error occurs when firefox was not shut down cleanly.  If you look in $HOME/.mozilla/firefox you'll see a directory named something.default.  Enter that directory and delete any "lock" and ".parentlock" files you see there:

```

cd ~
cd .mozilla/firefox
cd abcdefg.default
rm -f lock .parentlock

```Replace "abcdefg" with the name of the default directory on your system.

This problem doesn't occur as often as it once did, so Mozilla must have cleaned up some of the code that removes lock files.  But it does still happen as you have discovered, and it must cause novice users fits because the reason for the problem is so obscure.

I think rebooting may clean out the locks, but that's not an acceptable solution on *nix systems where rebooting is always the last resort.

Thunderbird can also fall victim to this problem, but it doesn't happen as often with TBird as it does with Firefox.
hi
thanks for reply. i just try to reproduce it again - gulp it dosen't happen. but you can
belive me. i tried it three times. close firefox -> close thunderbird.
start thunderbird -> open a mail with a hyperlink in it -> select that link -> got the error message.
sorry i forget to use the "fuser -u" command to figure out whats going on.
oh the lockfile ".parentlock" even exists when i quit firefox ( but without a process on it).
but thanks for reply. i will close that post.
cheers
hm as you can see my "ps -ef" gives me:
richi     4759     1 45 08:39 ?        00:00:04 /usr/lib/firefox/firefox [http://www.facebook.com/n/?notificat...n%40freenet.de]("http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de")
richi     4779     1  3 08:39 ?        00:00:00 /usr/lib/firefox/firefox [http://www.facebook.com/n/?notificat...n%40freenet.de]("http://www.facebook.com/n/?notifications&clk_loc=1&mid=77216e4G5af38c6ab00eG0Gd4&bcode=1.1359485366.AbmoSxiuF85kdv-S&n_m=rnerwein%40freenet.de")
richi     4826  4759  3 08:39 ?        00:00:00  /usr/lib/firefox/plugin-container  /usr/lib/flashplugin-installer/libflashplayer.so -greomni  /usr/lib/firefox/omn

thats 3 results - and what's the hell is going on with the "flashplugin" ??
i can't reproduce this behavior. if it happen again i'll will debug with more patience.
have a nice day

---

