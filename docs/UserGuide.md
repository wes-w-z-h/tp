---
layout: page
title: User Guide
---

## ConcertAddressBook

ConcertAddressBook is a **desktop app** for **Concert Organisers** to manage your Concert contacts, optimized for use via a Command Line Interface (CLI) with also a Graphical User Interface (GUI) in place to assist with information display. Manage your _contacts_ and _concerts_ in the book, finding contact information faster than your regular GUI contact management applications.

1. [Quick start](#Quick-Start)
2. [Features](#features)
   1. [Viewing help](#viewing-help--help)
   2. [Listing all persons](#listing-all-persons--list)
   3. [Adding a Person](#adding-a-person-addp)
   4. [Adding a Concert](#adding-a-concert-addc)
   5. [Adding a ConcertContact](#adding-a-concertcontact-addcc)
   6. [Deleting a person](#deleting-a-person--delete)
   7. [Deleting a concert](#deleting-a-concert--deletec)
   8. [Deleting a concertContact](#deleting-a-concertcontact--deletecc)
   9. [Clearing All Entries](#clearing-all-entries--clear)
   10. [Finding a person](#finding-a-person-findp)
   11. [Finding a concert](#finding-a-concert-findc)
   12. [Editing a person](#editing-a-person--edit)
   13. [Exiting programme](#exiting-the-program--exit)
3. [FAQ](#faq)
4. [Known Issues](#known-issues)
5. [Command Summary](#command-summary)

---

## Quick start

1. Ensure you have Java `17` or above installed in your Computer.

1. Download the latest `.jar` file from [here](https://github.com/AY2425S1-CS2103T-F11-1/tp/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your ConcertAddressBook.

1. Open a command terminal, `cd` into the folder you put the jar file in, and use the `java -jar concertphonebook.jar` command to run the application.<br>
   A GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

   - `list` : Lists all contacts.

   - `addp n/John Doe p/98765432 e/johnd@example.com a/311, Clementi Ave 2, #02-25 r/organiser t/friends` : Adds a contact named `John Doe` to the ConcertPhoneBook.

   - `addc n/Coachella a/81800 51st Ave, Indio, Southern California, United States d/2024-12-20 1010` : Adds a concert named `Coachella` to the ConcertPhoneBook.

   - `addcc 1 c/1` : Links the 1st person to the 1st concert

   - `deletep 1` : Deletes the 1st person shown in the current person list.

   - `deletec 1` : Deletes the 1st concert shown in the current concert list.

   - `deletecc 1 c/1` : Deletes the concertContact between the 1st person and 1st concert shown in the list.

   - `clear` : Deletes all contacts.

   - `findp n/alice bob charlie r/organiser` : Finds person(s) named either `Alice`, `Bob` or `Charlie` with an `organiser` role from the ConcertPhoneBook.

   - `findc n/coachella glastonbury` : Finds concert(s) named either `Coachella` or `Glastonbury` from the ConcertPhoneBook.

   - `exit` : Exits the app.

1. Refer to the [Features](#features) below for details of each command.

---

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

- Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

- Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

- Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

- Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

- Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

- If you are using a PDF version of this document, be careful when copying and pasting commands that span multiple lines as space characters surrounding line-breaks may be omitted when copied over to the application.
</div>

---

### Viewing help : `help`

Shows a message explaning how to access the help page (User Guide).

![help message](images/helpMessage.png)

Format: `help`

### Listing all persons : `list`

Shows a list of all persons in the Concert address book.

Format: `list`

### Adding a person: `addp`

Adds a person to the Concert Address book.

Format: `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS r/ROLE [t/TAG]…​`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
A person can have any number of tags (including 0)
</div>

Examples:

- `addp n/John Doe p/98765432 e/johnd@example.com a/John street, block 123, #01-01 r/Organiser`
- `addp n/Betsy Crowe t/friend e/betsycrowe@example.com a/Newgate Prison r/Artist p/1234567 t/criminal`

### Adding a Concert: `addc`

Adds a Concert to the Concert Address book.

Format: `addc n/CONCERTNAME a/ADDRESS d/DATE`

Examples:

- `addc n/Coachella a/81800 51st Ave, Indio, Southern California, United States d/2024-12-20 1010`

### Adding a ConcertContact: `addcc`

Adds an association to the contact in the Concert Address book with another Concert.

Format: `addcc INDEX c/CONCERT_INDEX`

- Adds an association between the person at the specified `INDEX` to the concert at the specified `CONCERT_INDEX`
- The index refers to the index number shown in the displayed person / concert list. The index **must be a positive integer** 1, 2, 3, …​

### Deleting a person : `deletep`

Deletes the specified person from the Concert address book.

Format: `deletep INDEX`

- Deletes the person at the specified `INDEX`.
- The index refers to the index number shown in the displayed person list.
- The index **must be a positive integer** 1, 2, 3, …​

Examples:

- `list` followed by `delete 2` deletes the 2nd person in the Concert address book.
- `find Betsy` followed by `delete 1` deletes the 1st person in the results of the `find` command.

### Deleting a concert : `deletec`

Deletes the specified person from the Concert address book.

Format: `deletec INDEX`

- Deletes the concert at the specified `INDEX`.
- The index refers to the index number shown in the displayed concert list.
- The index **must be a positive integer** 1, 2, 3, …​

### Deleting a concertContact : `deletecc`

Deletes the specified concertContact from the Concert address book.

Format: `deletecc PERSON_INDEX c/CONCERT_INDEX`

- Deletes the concertContact between the person in the specified `PERSON_INDEX` and the concert in the specified `CONCERT_INDEX`.
- The index refers to the index number shown in the displayed person / concert list.
- The index **must be a positive integer** 1, 2, 3, …​

### Clearing all entries : `clear`

Clears all entries from the Concert address book.

Format: `clear`

### Finding a person: `findp`

Finds persons whose names contain any of the given keywords.

Format: `findp [n/NAME_KEYWORDS] [r/ROLE]`

- The search is case-insensitive. e.g `hans` will match `Hans`
- The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
- Only full words will be matched e.g. `Han` will not match `Hans`
- Persons matching both name and role from the command entry will be returned (i.e. `OR` search).
  e.g. `findp n/Hans Bo r/Artist` will return `Hans Gruber, Artist` and `Bo Yang, Artist`
- At least one of the 2 fields must be present

Examples:

- `findp n/Alex Roy` finds person(s) with Alex or Roy in their names.
- `findp r/Artist` finds person(s) with a role of Artist.
- `findp n/Alex Roy r/Artist` finds person(s) with Alex or Roy in their names and has a role of Artist.

### Finding a concert: `findc`

Finds concerts whose names contain any of the given keywords.

Format: `findc n/NAME_KEYWORDS`

- The search is case-insensitive. e.g `coachella` will match `Coachella`
- The order of the keywords does not matter. e.g. `Coachella Glastonbury` will match `Glastonbury Coachella`
- Only full words will be matched e.g. `Coachell` will not match `Coachella`

Examples:

- `findc n/Coachella` finds concert(s) with Coachella in their names.

### Editing a person : `edit`

Edits an existing person in the Concert address book.

Format: `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [r/ROLE] [t/TAG]…​`

- Edits the person at the specified `INDEX`. The index refers to the index number shown in the displayed person list. The index **must be a positive integer** 1, 2, 3, …​
- At least one of the optional fields must be provided.
- Existing values will be updated to the input values.
- When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
- You can remove all the person’s tags by typing `t/` without
  specifying any tags after it.

Examples:

- `edit 1 p/91234567 e/johndoe@example.com` Edits the phone number and email address of the 1st person to be `91234567` and `johndoe@example.com` respectively.
- `edit 2 n/Betsy Crower t/` Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

### Exiting the program : `exit`

Exits the program.

Format: `exit`

### Saving the data

ConcertAddressBook data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the data file

ConcertAddressBook data are saved automatically as a JSON file `[JAR file location]/data/addressbook.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, ConcertPhonebook will discard all data and start with an empty data file at the next run. Hence, it is recommended to take a backup of the file before editing it.<br>
Furthermore, certain edits can cause ConcertPhonebook to behave in unexpected ways (e.g., if a value entered is outside the acceptable range). Therefore, edit the data file only if you are confident that you can update it correctly.
</div>

### Archiving data files `[coming in v2.0]`

---

## FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous AddressBook home folder.

---

## Known issues

1. **When using multiple screens**, if you move the application to a secondary screen, and later switch to using only the primary screen, the GUI will open off-screen. The remedy is to delete the `preferences.json` file created by the application before running the application again.
2. **If you minimize the Help Window** and then run the `help` command (or use the `Help` menu, or the keyboard shortcut `F1`) again, the original Help Window will remain minimized, and no new Help Window will appear. The remedy is to manually restore the minimized Help Window.

---

## Command summary

| Action                    | Format, Examples                                                                                                                                                             |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **List**                  | `list`                                                                                                                                                                       |
| **Add Person**            | `addp n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS r/ROLE [t/TAG]…​` <br> e.g., `add n/Alex Yeoh p/22224444 e/alexyeoh@example.com a/123, Clementi Rd, 1234665 r/Artist t/friend` |
| **Add Concert**           | `addc n/CONCERTNAME a/ADDRESS d/DATE `<br> e.g. `addc n/Coachella a/81800 51st Ave, Indio, Southern California, United States d/2024-12-20 1010`                             |
| **Add ConcertContact**    | `addcc INDEX c/CONCERT_INDEX`                                                                                                                                                |
| **Delete Person**         | `deletep INDEX`<br> e.g., `deletep 3`                                                                                                                                        |
| **Delete Concert**        | `deletep INDEX`<br> e.g., `deletec 3`                                                                                                                                        |
| **Delete ConcertContact** | `deletecc PERSON_INDEX c/CONCERT_INDEX`<br> e.g., `deletecc 3 c/3`                                                                                                           |
| **Clear**                 | `clear`                                                                                                                                                                      |
| **Edit**                  | `edit INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [a/ADDRESS] [t/TAG]…​`<br> e.g.,`edit 2 n/James Lee e/jameslee@example.com`                                                  |
| **Find Person**           | `findp [n/NAME_KEYWORDS] [r/ROLE]`<br> e.g., `find n/James Jake r/organiser`                                                                                                 |
| **Find Concert**          | `findc [n/NAME_KEYWORDS]`<br> e.g., `find n/Coachella Glastonbury`                                                                                                           |
| **Help**                  | `help`                                                                                                                                                                       |
