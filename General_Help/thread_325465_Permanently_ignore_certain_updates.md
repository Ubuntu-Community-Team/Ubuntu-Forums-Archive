---
title: "Permanently ignore certain updates"
date: 2006-12-25
forum: General Help
---

### Post by Super King on 2006-12-25
Is there any way I can the Update Manager in Ubuntu (Edgy) completely ignore certain updates. For example, there was a bunch of recent updatea for OpenOffice, which I no longer have installed (I removed it via Synaptic a while ago). Can I somehow block these updates from showing up in the Update Manager?

---

### Post by bulldog on 2006-12-25
You can lock the version in synaptic,so it wouldn't be upgrading again.
You have to do this for every application which you don't want to upgrade again.

---

### Post by az on 2006-12-25
> **Super King said:**
> Is there any way I can the Update Manager in Ubuntu (Edgy) completely ignore certain updates. For example, there was a bunch of recent updatea for OpenOffice, which I no longer have installed (I removed it via Synaptic a while ago). Can I somehow block these updates from showing up in the Update Manager?

If the application is removed using synaptic, you will no longer get updates for it.

Be aware that removing openoffice will remove the ubuntu-desktop metapackage.  A metapackage just depends on other packages so that you get the whole group just by installing the one package.  If you tried to re-install the ubuntu-desktop meta-package, you will end up installing openoffice again.

---

