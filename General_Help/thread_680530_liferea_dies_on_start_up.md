---
title: "liferea dies on start up"
date: 2008-01-28
forum: General Help
---

### Post by harrisony on 2008-01-28
Ok this is under Ubuntu 

On load of Liferea it always seg faults :( I don't think this is a bug because none of my friends have this problem and ive tried the latest version from source as well and that seg faulted.

All I remember is that i was sshing into my laptop and under X Forwarding I was adding some stuff to liferea and then i was annoyed at it and i did like 3 ctrl-c's (bad bad move) and ever since then it has died every time on load

Ive also removed my ./.lifera_1.4/ directory 

Here is the output from liferea --debug-all
```
TRACE: + rule_init

TRACE: - rule_init

TRACE: + db_init

DB: Opening DB file /home/harrisony/.liferea_1.4/liferea.db...

CACHE: Data base file /home/harrisony/.liferea_1.4/liferea.db was not found... Creating new one.

DB: current DB schema version: 5

DB: executing SQL: CREATE TABLE items (   title         TEXT,   read            INTEGER,   new          INTEGER,   updated             INTEGER,   popup                INTEGER,   marked               INTEGER,   source     TEXT,   source_id                TEXT,   valid_guid              INTEGER,   real_source_url      TEXT,   real_source_title      TEXT,   description     TEXT,   date            INTEGER,   comment_feed_id      INTEGER,   comment            INTEGER);

DB:  -> result: 1 (table items already exists)

DB: executing SQL: CREATE INDEX items_idx ON items (source_id);

DB:  -> result: 1 (index items_idx already exists)

DB: executing SQL: CREATE TABLE itemsets (   item_id            INTEGER,   node_id              TEXT,   read  INTEGER,   comment            INTEGER,   PRIMARY KEY (item_id, node_id));

DB:  -> result: 1 (table itemsets already exists)

DB: executing SQL: CREATE INDEX itemset_idx  ON itemsets (node_id);

DB:  -> result: 1 (index itemset_idx already exists)

DB: executing SQL: CREATE INDEX itemset_idx2 ON itemsets (item_id);

DB:  -> result: 1 (index itemset_idx2 already exists)

DB: executing SQL: CREATE TABLE metadata (   item_id            INTEGER,   nr                   INTEGER,   key                 TEXT,   value                   TEXT,   PRIMARY KEY (item_id, nr));

DB:  -> result: 1 (table metadata already exists)

DB: executing SQL: CREATE INDEX metadata_idx ON metadata (item_id);

DB:  -> result: 1 (index metadata_idx already exists)

DB: executing SQL: DROP TRIGGER item_removal;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TRIGGER item_removal DELETE ON itemsets BEGIN    DELETE FROM items WHERE ROWID = old.item_id;    DELETE FROM metadata WHERE item_id = old.item_id; END;

DB:  -> result: 0 (success)

DB: executing SQL: DROP TRIGGER item_insert;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TRIGGER item_insert INSERT ON items BEGIN    UPDATE itemsets SET read = new.read    WHERE item_id = new.ROWID; END;

DB:  -> result: 0 (success)

DB: executing SQL: DROP TRIGGER item_update;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TRIGGER item_update UPDATE ON items BEGIN    UPDATE itemsets SET read = new.read    WHERE item_id = new.ROWID; END;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TABLE subscription (   node_id            STRING,   source             STRING,   orig_source        STRING,   filter_cmd         STRING,   update_interval   INTEGER,   default_interval   INTEGER,   discontinued       INTEGER,   available          INTEGER,   PRIMARY KEY (node_id));

DB:  -> result: 1 (table subscription already exists)

DB: executing SQL: CREATE TABLE update_state (   node_id            STRING,   last_modified      STRING,   etag               STRING,   last_update        INTEGER,   last_favicon_update INTEGER,   PRIMARY KEY (node_id));

DB:  -> result: 1 (table update_state already exists)

DB: executing SQL: CREATE TABLE subscription_metadata (   node_id            STRING,   nr                 INTEGER,   key                TEXT,   value              TEXT,   PRIMARY KEY (node_id, nr));

DB:  -> result: 1 (table subscription_metadata already exists)

DB: executing SQL: CREATE INDEX subscription_metadata_idx ON subscription_metadata (node_id);

DB:  -> result: 1 (index subscription_metadata_idx already exists)

DB: executing SQL: DROP TRIGGER subscription_removal;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TRIGGER subscription_removal DELETE ON subscription BEGIN    DELETE FROM node WHERE node_id = old.node_id;    DELETE FROM update_state WHERE node_id = old.node_id;    DELETE FROM subscription_metadata WHERE node_id = old.node_id;    DELETE FROM itemsets WHERE node_id = old.node_id; END;

DB:  -> result: 0 (success)

DB: executing SQL: CREATE TABLE node (   node_id                STRING,   parent_id             STRING,   titleSTRING,   type          INTEGER,   expanded           INTEGER,   view_mode              INTEGER,   sort_columnINTEGER,   sort_reversed INTEGER,   PRIMARY KEY (node_id));

DB:  -> result: 1 (table node already exists)

DB: executing SQL: CREATE INDEX node_idx ON node (node_id);

DB:  -> result: 1 (index node_idx already exists)

DB: table setup took 0,293s

TRACE: - db_init

CONF: proxy auto detect is configured

CONF: no proxy GNOME of $http_proxy configuration found...

CONF: Proxy settings are now NULL:0 NULL:NULL

TRACE: + plugin_mgmt_get_init

PLUGINS: Scanning for plugins (/usr/lib/liferea):

PLUGINS: -> libnotify notification (liblinotiflibnotify.so, type=3)

PLUGINS: -> LUA Scripting Support Plugin (libliscrlua.so, type=4)

PLUGINS: -> Mozilla Rendering Plugin (liblihtmlm.so, type=0)

PLUGINS: using "Mozilla" for HTML rendering...

TRACE: + mozembed_init

TRACE: - mozembed_init

PLUGINS: using "libnotify" for notification type 0

TRACE: - plugin_mgmt_init

PLUGINS: using "LUA Scripting Support Plugin" for scripting...

TRACE: + ui_mainwindow_init

TRACE: + ui_feedlist_init

TRACE: - ui_feedlist_init

TRACE: + feedlist_init

CACHE: Setting up root node

TRACE: + node_source_setup_root

TRACE: + default_source_source_import

CACHE: Importing OPML file: /usr/share/liferea/opml/feedlist.opml

TRACE: + import_parse_outline

CACHE: -> must be a folder

GUI: adding node "international" as child of parent="root"

GUI: folder empty check for node id "galavmi"

GUI: folder empty check for node id "quycgxp"

TRACE: + import_parse_outline

CACHE: -> must be a folder

GUI: adding node "OSS" as child of parent="international"

GUI: folder empty check for node id "quycgxp"

GUI: folder empty check for node id "mkmttgp"

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription aaewdim update state (thread=0x80bdb58)

DB: Could not load update state for subscription aaewdim (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=art.gnome.org source=http://art.gnome.org/backend.php typeStr=(null) interval=-1

GUI: adding node "art.gnome.org" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: aaewdim and doing first download...

UPDATE: Scheduling art.gnome.org to be updated

DB: saving subscription aaewdim update state (thread=0x80bdb58)

DB: update state save took 0,366s

UPDATE: Resetting last poll counter to 1201502481.

UPDATE: processing request (http://art.gnome.org/backend.php)

UPDATE: downloading http://art.gnome.org/backend.php

NET: downloading url=/backend.php host=art.gnome.org

NET: NetConnect() (with getaddrinfo)

NET: host=art.gnome.org port=80

DB: updating node info aaewdim (thread 0x80bdb58)

DB: subscription_update took 0,194s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription rnsipae update state (thread=0x80bdb58)

DB: Could not load update state for subscription rnsipae (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Debian Package a Day source=http://debaday.debian.net/feed/atom/ typeStr=(null) interval=-1

GUI: adding node "Debian Package a Day" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: rnsipae and doing first download...

UPDATE: Scheduling Debian Package a Day to be updated

DB: saving subscription rnsipae update state (thread=0x80bdb58)

DB: update state save took 0,223s

UPDATE: Resetting last poll counter to 1201502481.

DB: updating node info rnsipae (thread 0x80bdb58)

DB: subscription_update took 0,238s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription lonoonw update state (thread=0x80bdb58)

DB: Could not load update state for subscription lonoonw (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Gnomefiles source=http://www.gnomefiles.org/files/gnomefiles.rdf typeStr=(null) interval=-1

GUI: adding node "Gnomefiles" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: lonoonw and doing first download...

UPDATE: Scheduling Gnomefiles to be updated

DB: saving subscription lonoonw update state (thread=0x80bdb58)

DB: update state save took 0,220s

UPDATE: Resetting last poll counter to 1201502482.

DB: updating node info lonoonw (thread 0x80bdb58)

DB: subscription_update took 0,196s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription bqlbeha update state (thread=0x80bdb58)

DB: Could not load update state for subscription bqlbeha (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=GNOME Footnotes source=http://www.gnomedesktop.org/backend.php typeStr=(null) interval=-1

GUI: adding node "GNOME Footnotes" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: bqlbeha and doing first download...

UPDATE: Scheduling GNOME Footnotes to be updated

DB: saving subscription bqlbeha update state (thread=0x80bdb58)

DB: update state save took 0,223s

UPDATE: Resetting last poll counter to 1201502482.

DB: updating node info bqlbeha (thread 0x80bdb58)

DB: subscription_update took 0,234s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription optpawe update state (thread=0x80bdb58)

DB: Could not load update state for subscription optpawe (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=GrokLaw source=http://www.groklaw.net/backend/GrokLaw.rdf typeStr=(null) interval=-1

GUI: adding node "GrokLaw" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: optpawe and doing first download...

UPDATE: Scheduling GrokLaw to be updated

DB: saving subscription optpawe update state (thread=0x80bdb58)

DB: update state save took 0,220s

UPDATE: Resetting last poll counter to 1201502483.

DB: updating node info optpawe (thread 0x80bdb58)

DB: subscription_update took 0,216s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription rgpffam update state (thread=0x80bdb58)

DB: Could not load update state for subscription rgpffam (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Linux.com source=http://www.linux.com/index.rss typeStr=(null) interval=-1

GUI: adding node "Linux.com" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: rgpffam and doing first download...

UPDATE: Scheduling Linux.com to be updated

DB: saving subscription rgpffam update state (thread=0x80bdb58)

DB: update state save took 0,224s

UPDATE: Resetting last poll counter to 1201502483.

DB: updating node info rgpffam (thread 0x80bdb58)

DB: subscription_update took 0,251s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription hgcjsbl update state (thread=0x80bdb58)

DB: Could not load update state for subscription hgcjsbl (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=mozillaZine source=http://www.mozillazine.org/contents.rdf typeStr=(null) interval=-1

GUI: adding node "mozillaZine" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: hgcjsbl and doing first download...

UPDATE: Scheduling mozillaZine to be updated

DB: saving subscription hgcjsbl update state (thread=0x80bdb58)

DB: update state save took 0,219s

UPDATE: Resetting last poll counter to 1201502484.

DB: updating node info hgcjsbl (thread 0x80bdb58)

DB: subscription_update took 0,196s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription xmvjgru update state (thread=0x80bdb58)

DB: Could not load update state for subscription xmvjgru (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Newsforge source=http://www.newsforge.com/newsforge.rss typeStr=(null) interval=-1

GUI: adding node "Newsforge" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: xmvjgru and doing first download...

UPDATE: Scheduling Newsforge to be updated

DB: saving subscription xmvjgru update state (thread=0x80bdb58)

DB: update state save took 0,227s

UPDATE: Resetting last poll counter to 1201502484.

DB: updating node info xmvjgru (thread 0x80bdb58)

DB: subscription_update took 0,251s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription stkiwed update state (thread=0x80bdb58)

DB: Could not load update state for subscription stkiwed (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Planet Debian source=http://planet.debian.org/rss20.xml typeStr=(null) interval=-1

GUI: adding node "Planet Debian" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: stkiwed and doing first download...

UPDATE: Scheduling Planet Debian to be updated

DB: saving subscription stkiwed update state (thread=0x80bdb58)

DB: update state save took 0,217s

UPDATE: Resetting last poll counter to 1201502484.

DB: updating node info stkiwed (thread 0x80bdb58)

DB: subscription_update took 0,203s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription ylcktau update state (thread=0x80bdb58)

DB: Could not load update state for subscription ylcktau (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=Slashdot source=http://slashdot.org/slashdot.rss typeStr=(null) interval=-1

GUI: adding node "Slashdot" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: ylcktau and doing first download...

UPDATE: Scheduling Slashdot to be updated

DB: saving subscription ylcktau update state (thread=0x80bdb58)

DB: update state save took 0,224s

UPDATE: Resetting last poll counter to 1201502485.

DB: updating node info ylcktau (thread 0x80bdb58)

DB: subscription_update took 0,251s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> URL found assuming type feed

DB: loading subscription wktucfw update state (thread=0x80bdb58)

DB: Could not load update state for subscription wktucfw (error code 101)!

TRACE: + favicon_load_from_cache

TRACE: - favicon_load_from_cache

CACHE: import feed: title=TuxMobil source=http://tuxmobil.org/tuxmobil_rss.rdf typeStr=(null) interval=-1

GUI: adding node "TuxMobil" as child of parent="OSS"

GUI: folder empty check for node id "mkmttgp"

CACHE: seems to be an import, setting new id: wktucfw and doing first download...

UPDATE: Scheduling TuxMobil to be updated

DB: saving subscription wktucfw update state (thread=0x80bdb58)

DB: update state save took 0,219s

UPDATE: Resetting last poll counter to 1201502485.

DB: updating node info wktucfw (thread 0x80bdb58)

DB: subscription_update took 0,196s

TRACE: - import_parse_outline

CACHE: seems to be an import, setting new id: mkmttgp and doing first download...

DB: updating node info mkmttgp (thread 0x80bdb58)

DB: subscription_update took 0,318s

TRACE: - import_parse_outline

CACHE: seems to be an import, setting new id: quycgxp and doing first download...

DB: updating node info quycgxp (thread 0x80bdb58)

DB: subscription_update took 0,263s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> node type tag found: "vfolder"

CACHE: import vfolder: title=Unread

TRACE: + vfolder_new

TRACE: - vfolder_new

CACHE: loading rule "unread" ""

GUI: adding node "Unread" as child of parent="root"

GUI: folder empty check for node id "galavmi"



** (liferea-bin:14093): WARNING **: Dropping view failed (no such table: view_errvxau) SQL: DROP VIEW view_errvxau;

DB: Creating view errvxau: CREATE VIEW view_errvxau AS SELECT items.ROWID AS item_id,items.read AS item_read FROM items   WHERE items.read = 0 AND items.comment != 1;

CACHE: seems to be an import, setting new id: errvxau and doing first download...

DB: updating node info errvxau (thread 0x80bdb58)

NET: successfully connected socket 27

NET: writing 164 bytes to socket 27

DB: subscription_update took 0,616s

TRACE: - import_parse_outline

TRACE: + import_parse_outline

CACHE: -> node type tag found: "vfolder"

CACHE: import vfolder: title=Important

TRACE: + vfolder_new

TRACE: - vfolder_new

CACHE: loading rule "flagged" ""

GUI: adding node "Important" as child of parent="root"

GUI: folder empty check for node id "galavmi"



** (liferea-bin:14093): WARNING **: Dropping view failed (no such table: view_uulvpmd) SQL: DROP VIEW view_uulvpmd;

DB: Creating view uulvpmd: CREATE VIEW view_uulvpmd AS SELECT items.ROWID AS item_id,items.read AS item_read FROM items   WHERE items.marked = 1 AND items.comment != 1;

CACHE: seems to be an import, setting new id: uulvpmd and doing first download...

DB: updating node info uulvpmd (thread 0x80bdb58)

DB: subscription_update took 0,262s

TRACE: - import_parse_outline

DB: checking for lost subscriptions...

TRACE: - default_source_source_import

TRACE: - node_source_setup_root

CACHE: Initializing node state

GUI: Notification setup

UPDATE: Performing initial feed update

UPDATE: initial update: using auto update

CONF: Scheduling feedlist save

TRACE: - feedlist_init

GUI: Setting item list visibility mode: 2

Segmentation fault (core dumped)


```
Thanks for any help :KS

---

