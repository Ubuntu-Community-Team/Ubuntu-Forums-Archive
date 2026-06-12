---
title: "Cant compile Cockatrice on 14.04 (magic the gathering) Help!!"
date: 2014-04-20
forum: General Help
---

### Post by blossomrevane on 2014-04-20
I am using the source from Woogerworks.com to install cockatrice. I have all the dependencies as far as I am aware, but it wont seem to work. I get a error saying that qtmultimedia library not found but I am pretty sure that I have it. Here is what I am seeing:

```

blossom@GLaDOS:~$ cd '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice' 
blossom@GLaDOS:~/Downloads/Cockatrice_git-20140115-92ff503/cockatrice$ mkdir build
mkdir: cannot create directory &#8216;build&#8217;: File exists
blossom@GLaDOS:~/Downloads/Cockatrice_git-20140115-92ff503/cockatrice$ cd build
blossom@GLaDOS:~/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build$ cmake ..
-- Using QtMobility version: system's default
Qt QTMULTIMEDIA library not found.
-- Configuring done
-- Generating done
-- Build files have been written to: /home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build
blossom@GLaDOS:~/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build$ make
[  1%] Generating src/moc_pending_command.cxx
[  1%] Generating version_string.cpp, version_string.h
-- Found Git: /usr/bin/git (found version "1.9.1") 
[  1%] Generating cockatrice_de.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_de.qm'...
    Generated 791 translation(s) (791 finished and 0 unfinished)
[  2%] Generating cockatrice_en.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_en.qm'...
    Generated 9 translation(s) (7 finished and 2 unfinished)
    Ignored 782 untranslated source text(s)
[  2%] Generating cockatrice_es.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_es.qm'...
    Generated 791 translation(s) (791 finished and 0 unfinished)
[  3%] Generating cockatrice_it.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_it.qm'...
    Generated 791 translation(s) (791 finished and 0 unfinished)
[  3%] Generating cockatrice_ja.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_ja.qm'...
    Generated 659 translation(s) (578 finished and 81 unfinished)
    Ignored 132 untranslated source text(s)
[  4%] Generating cockatrice_pt.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_pt.qm'...
    Generated 791 translation(s) (791 finished and 0 unfinished)
[  4%] Generating cockatrice_sv.qm
Updating '/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build/cockatrice_sv.qm'...
    Generated 791 translation(s) (791 finished and 0 unfinished)
[  4%] Generating qrc_cockatrice.cxx
[  5%] Generating src/moc_abstractcounter.cxx
[  5%] Generating src/moc_counter_general.cxx
[  6%] Generating src/moc_dlg_creategame.cxx
[  6%] Generating src/moc_dlg_filter_games.cxx
[  7%] Generating src/moc_dlg_connect.cxx
[  7%] Generating src/moc_dlg_create_token.cxx
[  7%] Generating src/moc_dlg_edit_tokens.cxx
[  8%] Generating src/moc_gamesmodel.cxx
[  8%] Generating src/moc_abstractclient.cxx
[  9%] Generating src/moc_remoteclient.cxx
[  9%] Generating src/moc_window_main.cxx
[ 10%] Generating src/moc_cardzone.cxx
[ 10%] Generating src/moc_selectzone.cxx
[ 10%] Generating src/moc_player.cxx
[ 11%] Generating src/moc_playertarget.cxx
[ 11%] Generating src/moc_abstractcarditem.cxx
[ 12%] Generating src/moc_carditem.cxx
[ 12%] Generating src/moc_tablezone.cxx
[ 13%] Generating src/moc_handzone.cxx
[ 13%] Generating src/moc_handcounter.cxx
[ 13%] Generating src/moc_carddatabase.cxx
[ 14%] Generating src/moc_gameview.cxx
[ 14%] Generating src/moc_gameselector.cxx
[ 15%] Generating src/moc_decklistmodel.cxx
[ 15%] Generating src/moc_deck_loader.cxx
[ 16%] Generating src/moc_dlg_load_deck_from_clipboard.cxx
[ 16%] Generating src/moc_dlg_load_remote_deck.cxx
[ 16%] Generating src/moc_cardinfowidget.cxx
[ 17%] Generating src/moc_messagelogwidget.cxx
[ 17%] Generating src/moc_zoneviewzone.cxx
[ 18%] Generating src/moc_zoneviewwidget.cxx
[ 18%] Generating src/moc_pilezone.cxx
[ 19%] Generating src/moc_stackzone.cxx
[ 19%] Generating src/moc_carddragitem.cxx
[ 19%] Generating src/moc_carddatabasemodel.cxx
[ 20%] Generating src/moc_setsmodel.cxx
[ 20%] Generating src/moc_window_sets.cxx
[ 21%] Generating src/moc_abstractgraphicsitem.cxx
[ 21%] Generating src/moc_abstractcarddragitem.cxx
[ 22%] Generating src/moc_dlg_settings.cxx
[ 22%] Generating src/moc_dlg_cardsearch.cxx
[ 22%] Generating src/moc_phasestoolbar.cxx
[ 23%] Generating src/moc_gamescene.cxx
[ 23%] Generating src/moc_arrowitem.cxx
[ 24%] Generating src/moc_arrowtarget.cxx
[ 24%] Generating src/moc_tab.cxx
[ 25%] Generating src/moc_tab_server.cxx
[ 25%] Generating src/moc_tab_room.cxx
[ 25%] Generating src/moc_tab_message.cxx
[ 26%] Generating src/moc_tab_game.cxx
[ 26%] Generating src/moc_tab_deck_storage.cxx
[ 27%] Generating src/moc_tab_replays.cxx
[ 27%] Generating src/moc_tab_supervisor.cxx
[ 28%] Generating src/moc_tab_admin.cxx
[ 28%] Generating src/moc_tab_userlists.cxx
[ 28%] Generating src/moc_tab_deck_editor.cxx
[ 29%] Generating src/moc_replay_timeline_widget.cxx
[ 29%] Generating src/moc_deckstats_interface.cxx
[ 30%] Generating src/moc_chatview.cxx
[ 30%] Generating src/moc_userlist.cxx
[ 31%] Generating src/moc_userinfobox.cxx
[ 31%] Generating src/moc_user_context_menu.cxx
[ 31%] Generating src/moc_remotedecklist_treewidget.cxx
[ 32%] Generating src/moc_remotereplaylist_treewidget.cxx
[ 32%] Generating src/moc_deckview.cxx
[ 33%] Generating src/moc_playerlistwidget.cxx
[ 33%] Generating src/moc_settingscache.cxx
[ 34%] Generating src/moc_localserver.cxx
[ 34%] Generating src/moc_localserverinterface.cxx
[ 34%] Generating src/moc_localclient.cxx
[ 35%] Generating src/moc_priceupdater.cxx
[ 35%] Generating src/moc_soundengine.cxx
Scanning dependencies of target cockatrice
[ 35%] Building CXX object CMakeFiles/cockatrice.dir/src/abstractcounter.cpp.o
In file included from /home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/src/abstractcounter.cpp:2:0:
/home/blossom/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/src/player.h:8:30: fatal error: pb/game_event.pb.h: No such file or directory
 #include "pb/game_event.pb.h"
                              ^
compilation terminated.
make[2]: *** [CMakeFiles/cockatrice.dir/src/abstractcounter.cpp.o] Error 1
make[1]: *** [CMakeFiles/cockatrice.dir/all] Error 2
make: *** [all] Error 2
blossom@GLaDOS:~/Downloads/Cockatrice_git-20140115-92ff503/cockatrice/build$
```

---

