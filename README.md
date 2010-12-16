# Bash Encryption

These scripts can be used to create, read, and edit encrypted text
files.

This is useful for sharing data on [Dropbox](http://www.dropbox.com)
that doesn’t change very often. [TrueCrypt](http://www.truecrypt.org/)
is annoying for this because of mount/dismount and timestamp issues.
Word/Excel encryption is unreliable across platforms and versions.

## Command-line usage

To create a new blank encrypted text file :

    ./new [filename]

To decrypt the file to stdout :

    ./read [filename]

To decrypt / edit / encrypt using $EDITOR :

    ./edit [filename]

To change the pass phrase :

    ./rekey [filename]

When the optional filename argument is not supplied, the scripts
default to using a file called “data” in the same directory as the
scripts.

## GUI usage

There are also two scripts which are meant to be run from the Mac
Finder for people who aren’t UNIX-savvy. The default text editor on
Mac OS X is generally TextEdit.app. It’s possible these scripts would
also work with NextStep. They can be double-clicked to edit the
default “data” file. You’d probably want to wrap them for each
encrypted file if you have more than one encrypted file that GUI users
need to deal with.

To read the file in the default text editor :

    ./read_with_textedit [filename]

To edit the file in the default text editor :

    ./edit_with_textedit [filename]

If you’re using Dropbox, be sure you have 0.8 or newer to ensure that
the executable attributes sync or these scripts will not work
correctly.

## Plaintext disclosure risk

The scripts make every effort to avoid the file system; however, temp
files are necessary for editing and for using TextEdit.

When temp files are used, the scripts make very effort to delete those
temp files. Be aware that SIGKILL cannot be handled and could leave
sensitive plaintext in your temp directory.

There is also the distinct possibility of user error resulting in
plaintext disclosure when using TextEdit. Even though the script
deletes the backing temp file used for read_with_textedit, the user
could still very conceivably save the file, leaving sensitive
plaintext in the temp directory.

## Sample data

The sample data file uses the passphrase “asdf!1234”.

## Pass phrases

You should choose a strong pass phrase. I suggest using
[Diceware](http://world.std.com/~reinhold/diceware.html) to generate a
5-word or better pass phrase for sensitive information.
