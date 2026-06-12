---
title: "Is this possible in Feisty? Keyboard language switching, Foobar rival AND...?"
date: 2007-05-13
forum: General Help
---

### Post by nightfire117 on 2007-05-13
I'm mostly a Windows user, for only a few reasons:

1.) I am more familiar with it
2.) Foobar2000 runs nicely (and actually has Last.FM and Unicode support and more format support than most Linux audio players), better than in Wine (same with Photoshop, as far as I know)
3.) Keyboard language switching: I can switch between English, pinyin input for Chinese (PRC), and Japanese (Microsoft IME, since I don't have a Japanese keyboard and can't input it directly that way).

My question is does Feisty have capabilities similar to Windows' keyboard language switching? I've done it under Dapper but only switched between, for example, Chinese and English, when I had the Chinese interface on. (i.e. I need to switch between all three layouts, in an English interface)

As for a Foobar2000 equivalent, it's obviously hands-down the best music playing software available. Is there anything that has: 1.) Mass tagging support (simultaneously tag multiple files - refer to Foobar2000's tagging system), 2.) supports Unicode files *and* ID3 tags, 3.) built-in Last.FM support (or at least some kind of plugin for it), 4.) FLAC, WMA support? I know I can Wine Foobar but I would rather not have to, since it's pretty unstable.

Video-playing software with lots of codec support, i.e. VLC is already available, although I've had strange bugs occur when using it under Ubuntu and playing MKV files.

Erm, otherwise these are the only things keeping me from using Ubuntu full-time. I'd much appreciate if anyone can help point out some programs and methods, because I'm starting to get tired of Windows, and want to use Ubuntu (Feisty or future releases, mainly) on my main PC and notebook.

[I don't know where to post this, so please move it if it's in the wrong place.]

~Nightfire

---

### Post by tgoose on 2007-05-13
> **nightfire117 said:**
> I'm mostly a Windows user, for only a few reasons:

1.) I am more familiar with it
2.) Foobar2000 runs nicely (and actually has Last.FM and Unicode support and more format support than most Linux audio players), better than in Wine (same with Photoshop, as far as I know)
3.) Keyboard language switching: I can switch between English, pinyin input for Chinese (PRC), and Japanese (Microsoft IME, since I don't have a Japanese keyboard and can't input it directly that way).

My question is does Feisty have capabilities similar to Windows' keyboard language switching? I've done it under Dapper but only switched between, for example, Chinese and English, when I had the Chinese interface on. (i.e. I need to switch between all three layouts, in an English interface)

I don't think you can switch to a specific layout in one press like in Windows, but there is a key combination to cycle between them so it's never more than two presses to swap between three layouts (mine is set to Alt+Alt Gr).

> 
As for a Foobar2000 equivalent, it's obviously hands-down the best music playing software available. Is there anything that has: 1.) Mass tagging support (simultaneously tag multiple files - refer to Foobar2000's tagging system), 2.) supports Unicode files *and* ID3 tags, 3.) built-in Last.FM support (or at least some kind of plugin for it), 4.) FLAC, WMA support? I know I can Wine Foobar but I would rather not have to, since it's pretty unstable.

Quod Libet is the closest thing to foobar2000 I've seen. It certainly lacks the vast number of plugins, but I've never found that a problem.

Mass tagging is less sophisticated than fb2k but I tend to be able to use it more quickly (apart from having to click save and close separately!)

I know very little about Unicode, but I think I *read* that Quod Libet's support is fine. All my ID3s certainly display!

last.fm is one of the plugins that comes in the vast quodlibet-plugins package and works fine.

FLAC works out of the box (as with most other linux players). I don't have any WMA to test but it at least claims to support it ("Supported formats: mod, mp3, mpc, trueaudio, wav, wavpack, wma, xiph"), but I probably had to install a plugin to do that.

> 
Video-playing software with lots of codec support, i.e. VLC is already available, although I've had strange bugs occur when using it under Ubuntu and playing MKV files.

I'm not too keen on the default Ubuntu player Totem, and having replaced it with VLC I've had no problems watching anything. Some people have said mplayer (or gmplayer, I forget the package name) can succeed where VLC fails, but having never had a problem I've never needed to investigate.

> 
Erm, otherwise these are the only things keeping me from using Ubuntu full-time. I'd much appreciate if anyone can help point out some programs and methods, because I'm starting to get tired of Windows, and want to use Ubuntu (Feisty or future releases, mainly) on my main PC and notebook.

[I don't know where to post this, so please move it if it's in the wrong place.]

~Nightfire

I'd definitely advise giving the Feisty live CD a spin and seeing if you like it. You can set it up before committing to an install if you want to see if it's up to scratch. 

Good luck!

---

### Post by hugmenot on 2007-05-13
> **tgoose said:**
> 
I know very little about Unicode, but I think I *read* that Quod Libet's support is fine. All my ID3s certainly display!

Unicode is supported across the board.
> 
FLAC works out of the box (as with most other linux players). I don't have any WMA to test but it at least claims to support it ("Supported formats: mod, mp3, mpc, trueaudio, wav, wavpack, wma, xiph"), but I probably had to install a plugin to do that.

You'll have to install a Quod Libet newer than the one from the repos to get WMA.
I put packages of QL 1.0 here: [http://ubuntuforums.org/showpost.php?p=2596985&postcount=201](http://ubuntuforums.org/showpost.php?p=2596985&postcount=201)

> 
I'm not too keen on the default Ubuntu player Totem, and having replaced it with VLC I've had no problems watching anything. Some people have said mplayer (or gmplayer, I forget the package name) can succeed where VLC fails, but having never had a problem I've never needed to investigate.


And it supports MKV fine. I recently watched a video with lot's of stream features that were all functioning.

---

### Post by strabes on 2007-05-13
Amarok does everything you asked for and more. You can install (global) support for basically any codec that exists. ubuntu-restricted-extras has all of this. For amarok you'll need to install libxine-extracodecs to play proprietary formats. Quod libet is very lightweight and is good if you're using Gnome. Amarok is a kde app so if you're using gnome you'll have to download lots of kde libs. (apt-get or synaptic will handle all of that for you automatically)

---

### Post by nightfire117 on 2007-05-13
Thanks for the info, guys.

> **tgoose said:**
> I don't think you can switch to a specific layout in one press like in Windows, but there is a key combination to cycle between them so it's never more than two presses to swap between three layouts (mine is set to Alt+Alt Gr).

That's quite good news. I'll investigate this further. 

> Unicode is supported across the board. Glad to hear that. I've used Amarok before but found it too resource-heavy for my liking. I don't like using libraries for my music, since I can manage it just fine with the file structure I organize my music with, and that extra bloat is unnecessary. I'll see if Quod Libet has album art support or a plugin for it, since I name my album art to "folder.jpg" and it displays in Foobar.

I'll check these things out, and I'm downloading the Feisty Live CD right now. (I intend to install it on my PC first and see if I want it on my notebook.) Thanks for the comments, guys.

~Nightfire

---

### Post by hugmenot on 2007-05-14
Well, QL uses a library and I know from my own experience that you cannot use your file system layout for anything useful. There's nothing like the "directory structure" setting in the Foobar album list. QL&#8217;s album list is flat.
Consider, however, that QL is the only player that respects all tags and not only the most &#8220;canonical&#8221; ones.

But about album art, you are completely set up with folder.jpgs. There&#8217;s also a plugin for Amazon&#8217;s web services.

---

### Post by nightfire117 on 2007-05-19
> **hugmenot said:**
> Well, QL uses a library and I know from my own experience that you cannot use your file system layout for anything useful. There's nothing like the "directory structure" setting in the Foobar album list. QL&#8217;s album list is flat.
Consider, however, that QL is the only player that respects all tags and not only the most &#8220;canonical&#8221; ones.

But about album art, you are completely set up with folder.jpgs. There&#8217;s also a plugin for Amazon&#8217;s web services.

I have found that it does use a library. On a secondary HDD I have installed Feisty just last night. So far, so good, and I have the languages set up so I can type them - the Chinese input system is even better than in Windows, in my opinion. That's a very good and convenient thing.

As for "[my] own filesystem," it's just the way I choose to organize my music files and folders. Well, I guess it's a downside that the album list is flat but you're right, it's still a good deal since it recognizes tags and such. Glad to hear that my folder.jpg files are useful. Well, I guess I'll play around with Feisty a bit more. Thanks for all the tips guys, you've helped a lot.

~Nightfire

[EDIT]: Been using Feisty for a few days. Trying to get NTFS write to work - otherwise I have English, Chinese and Japanese input, Quod Libet which supports playlists and is very nice so far, and pretty much everything I want in Ubuntu Feisty. Just a couple things that need to be tested, such as Wine compatibility with Photoshop and some other stuff (and hopefully Gaim/Pidgin or another IM client with voice + video support across MSN contacts - hopefully no need for Wine) and UT2004 would be good.

~Nightfire

---

