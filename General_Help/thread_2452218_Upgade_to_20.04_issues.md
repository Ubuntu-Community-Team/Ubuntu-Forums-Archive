---
title: "Upgade to 20.04 issues"
date: 2020-10-19
forum: General Help
---

### Post by jbjbjb2 on 2020-10-19
Let me apologize upfront for the length of this post, but there are a couple of different things going on here.

I just updated my laptop from 18.04 to 20.04. multiple times the update manager showed "update available", but each time it would quit on its own. No big deal, I decided to do the update through command line. And, because I have never had a single issue before, I didn't do a backup first :mad:. Anyway, update went fine until the reboot, then black screen with only a cursor. Boot failure, no problem, plug in a USB boot repair, still no startup. I then made a 20.04 Live USB and booted from that. After I got my computer running live I checked my hard drive for my files and found them to be intact. Running from the Live USB I backed up the whole hard drive using Deja Dup. Backup completed I continued to do the upgrade off of the Live USB with internet connection for any updates that may be needed. The strange thing about this was that I could not just replace the command line installation that I a originally installed, but instead has to reformat and re-partition the hard drive to get it to finally work. If someone has an idea of why this would happen I would like to hear it.

Secondly, and of a much greater concern is the backed up data. Dejadup could not restore the data!! Every time I pointed it at the date it came back with an error "no backup to restore. Apparently it did not generate a "time" file so it could not restore the data. Many hours of research brought me to to a post on Stack Exchange on manually rebuilding the backup files with some code by Hamish Downer, the first part ,   

```
for f in duplicity-full.*.difftar.gz; do echo "$f"; tar xf "$f"; done
```
unpacks all of the files in one session. This seemed to work well, but with almost 400 files took about 40 hrs to complete.The second part,


```
#!/usr/bin/env python3
import argparse
from pathlib import Path
import shutil
import sys


class FileReconstructor():

    def __init__(self, unpacked_dir, restore_dir):
        self.unpacked_path = Path(unpacked_dir).resolve()
        self.restore_path = Path(restore_dir).resolve()

    def reconstruct_files(self):
        for leaf_dir in self.walk_unpacked_leaf_dirs():
            target_path = self.target_path(leaf_dir)
            target_path.parent.mkdir(parents=True, exist_ok=True)
            with target_path.open('wb') as target_file:
                self.copy_file_parts_to(target_file, leaf_dir)

    def copy_file_parts_to(self, target_file, leaf_dir):
        file_parts = sorted(leaf_dir.iterdir(), key=lambda x: int(x.name))
        for file_part in file_parts:
            with file_part.open('rb') as source_file:
                shutil.copyfileobj(source_file, target_file)

    def walk_unpacked_leaf_dirs(self):
        """
        based on the assumption that all leaf files are named as numbers
        """
        seen_dirs = set()
        for path in self.unpacked_path.rglob('*'):
            if path.is_file():
                if path.parent not in seen_dirs:
                    seen_dirs.add(path.parent)
                    yield path.parent

    def target_path(self, leaf_dir_path):
        return self.restore_path / leaf_dir_path.relative_to(self.unpacked_path)


def parse_args(argv):
    parser = argparse.ArgumentParser()
    parser.add_argument(
        'unpacked_dir',
        help='The directory with the unpacked tar files',
    )
    parser.add_argument(
        'restore_dir',
        help='The directory to restore files into',
    )
    return parser.parse_args(argv)


def main(argv):
    args = parse_args(argv)
    reconstuctor = FileReconstructor(args.unpacked_dir, args.restore_dir)
    return reconstuctor.reconstruct_files()


if __name__ == '__main__':
    sys.exit(main(sys.argv[1:]))
```

is supposed to reconstruct and recreate the files. My real problem comes in at the first couple of lines on the second part. The second line
"import argparse" hangs immediately.The python3 executable is located "/usr/bin" where it should be at, and argparse is located in "/usr/local/lib/python3.8/dist-packages"
Both of them should be where they came from in the distribution.

Probably 99% of the stuff in those files I don't need, but any help getting back that one percent would be greatly appreciated.

Again, I apologize for the long post.

---

