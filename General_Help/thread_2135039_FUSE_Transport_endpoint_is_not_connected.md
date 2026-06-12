---
title: "FUSE Transport endpoint is not connected"
date: 2013-04-13
forum: General Help
---

### Post by reastland on 2013-04-13
I'm working on a homework assignment implementing the FUSE file system. I think that I have it pretty well set up, but I keep getting the following error message:

Could not display "/home/user/Dropbox/OpSys/pa4/MountDir".
Error: Error when getting information for file '/home/user/Dropbox/OpSys/pa4/MountDir': Transport endpoint is not connected
Please select another viewer and try again.

Before I run the program, I have two folders, MirrorDir and MountDir, both in a common folder. I pass these as command line arguments. Obviously, the MountDir is the mount point. Immediately when I execute the program, the MountDir folder disappears as a folder in my folder viewer. It simultaneously reappears as a mounted disk under Computer in the left panel below other folders like Home, Desktop, Documents, etc.  There is an eject arrow to its right. This looks like it is working. However, when I click on MountDir, I get the previously mentioned error.

This is the main function that I am using to start all of this:

```
int main(int argc, char *argv[])
{
    int fuse_stat;
    struct bb_state *bb_data;


    bb_data = malloc(sizeof(struct bb_state));
    if (bb_data == NULL) {
        perror("main calloc");
        abort();
    }


    // Pull the rootdir out of the argument list and save it in my
        // internal data
        bb_data->rootdir = realpath(argv[argc-2], NULL);
        argv[argc-2] = argv[argc-1];
        argv[argc-1] = NULL;
        argc--;


    // generate output to confirm that the two directories are intact
    size_t i;
    fprintf(stderr, "Confirming Mirrored directory: ");   
    for (i=0; i<strlen(bb_data->rootdir); i++) {
        fprintf(stderr, "%c", bb_data->rootdir[i]);
    }
    fprintf(stderr, "\n");


    fprintf(stderr, "Confirming Mount directory: ");
    for (i=0; i<strlen(argv[argc-1]); i++) {
        fprintf(stderr, "%c", argv[argc-1][i]);
    }
    fprintf(stderr, "\n");


    // turn over control to fuse
    fprintf(stderr, "about to call fuse_main\n");    
    fuse_stat = fuse_main(argc, argv, &xmp_oper, bb_data);
    fprintf(stderr, "fuse_main returned %d\n", fuse_stat);
    return fuse_stat;
}

```

The printf output looks perfect, but somehow this isn't mounting correctly. Can anyone see why? Thank you!

---

### Post by Habitual on 2013-04-14
n/m.
Way out of my league.

---

