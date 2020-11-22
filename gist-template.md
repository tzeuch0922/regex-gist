# Regex Gist

A Github Gist for describing how to use Regex(Regular Expressions). Regular expressions are used for identifying general text that follows specific parameters.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.    

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

#### Quick Reference

| Anchor   | Description     |
|:--------:|:----------------|
| ^        | Start of String |
| $        | End of String   |

#### Start of String

Used to make sure that your regular expression has to start at the beginning of the string.

Example:
```
^[a-z]
```
This regex would pass if the string starts with a lowercase letter.

#### End of String

Used to make sure that the regular expression is going to look from the end of the string.

Example:
```
[0-9]$
```
This regex would pass if the string ends with a number.

### Quantifiers

| Quantifier | Description               |
|:----------:|:--------------------------|
| *          | Match zero or more times  |
| +          | Match one or more times   |
| ?          | Match zero or one time    |
| {x,y}      | Matches from x to y times |

#### Match Zero or More Times

Used to match a character or sequence zero or more times.

Example:
```
^[\d]*[a-z]
```
This regex would pass if the string starts with zero or more numbers followed by a lowercase letter.

#### Match One or More Times

Used to match a character or sequence one or more times.

Example:
```
^[a-z]+[\d]
```
This regex would pass if the string starts with one or more lowercase letters followed by a number.

#### Match Zero or One Time

Used to match a character or sequence one or zero times.

Example:
```
^[A-Z]?[a-z]
```
This regex would pass if the string starts with zero or one uppercase letter followed by a lowercase letter.

#### Matches from x to y Times

Used to match a character or sequence at least x times, up to y times. It can also be used for exact number of matches, up to a specific number of matches, or at least a specific number of matches.

Examples:
```
[a-z]{4}
```
This regex would pass if the string includes 4 lowercase letters in a row.
```
[\d]{3, 10}[a-z]
```
This regex would pass if there was at least 3 numbers in a row, up to 10 followed by a lowercase letter.
```
[a-z]{4,}[\d]
```
This regex would pass if there was at least 4 lowercase letters in a row followed by a number.
```
[\d][A-Z]{,5}[a-z]
```
This regex would pass if there was a number followed by up to 5 uppercase letters followed by a lowercase letter.

### OR Operator

| Operator | Description        |
|:--------:|:-------------------|
| \|       | Match One or Other |

#### Match One or Other

Used to match one of two characters or patterns.

Example:
```
(22|33)$
```
This regex would pass if the string ended in 22 or 33.

### Character Classes

| Character Class | Description                     |
|:---------------:|:--------------------------------|
| \d              | Includes all numbers.           |
| \h              | Includes both space and tabs.   |
| \s              | Includes all whitespace.        |
| \w              | Includes all word characters.   |
| \l              | Includes all lowercase letters. |
| \u              | Includes all uppercase letters. |

#### Includes All Numbers

A character class that matches all numerical digits 0 through 9.

Example:
```
^[\d]
```
This regex would pass if the string started with a number.

#### Includes Both Space and Tabs

A character class that matches both space and tab characters.

Example:
```
[a-z][\h][a-z]
```
This regex would pass if a single space or tab existed between two lowercase letters in the string.

#### Includes All Whitespace

A character class that matches all whitespace characters, including new line characters.

Example:
```
[\s][A-Z]
```
This regex would pass if a capital letter followed a space, tab, or new line character.

#### Includes All Word Characters

A character class that matches all numbers, letters, and underscores.

Example:
```
[\w]+\.com
```
This regex would pass if the string included any assortment of numbers, letters, or underscores followed by .com.

#### Includes All Lowercase Letters

A character class that matches all lowercase letters.

Example:
```
[A-Z][\l]+
```
This regex would pass if the string included an uppercase letter followed by at least one lowercase letter.

#### Includes All Uppercase Letters

A character class that matches all uppercase letters.

Example:
```
([\u][a-z]+\h)+
```
This regex would pass if the string included at least one instance of a capitalized word followed by a space or tab.

### Flags

| Flags | Modes             | Description                                                             |
|:-----:|:------------------|:------------------------------------------------------------------------|
| i     | Case-insensitive  | Uppercase matches lowercase also and lowercase matches uppercase also.  |
| g     | Global Mode       | Looks for all matches. By default only looks for first match in string. |
| m     | Multiline mode    | The ^ character can match start of line and $ can match end of line.    |
| s     | Dotall mode       | Allows a . to match newline character. (\n)                             |

#### Case-insensitive

Makes the regular expression case-insensitive, allowing uppercase and lowercase to be interchangeable in the pattern.

Example:
```
^[a-z](/i)
```
This regex will match any string that starts with any letter.

#### Global Mode

Makes the regular expression match all occurences of the pattern instead of just the first.

Example:
```
[a-z]{4}(/g)
```
This regex will match every occurence of 4 lowercase letters in a row within a string.

#### Multiline Mode

Makes the regular expression allow ^ to match beginning of line also and $ to match end of line also.

Example:
```
^[\d](/m)
```
This regex will match any string that has a line that starts with a number.

#### Dotall Mode

Makes the regular expression allow a . character to match a new line character.

Example:
```
^[a-z](/ms)
```
This regex will match any string that has a line that starts with a lowercase letter at the beginning of a line or following a dot.

### Grouping and Capturing

| Expression | Description         |
|:----------:|:--------------------|
| (abc)      | Capturing Group     |
| (?:abc)    | Non-capturing Group |

#### Capturing Group

Used to group a set of characters or pattern together and will capture everything in it normally when executed.

Example:
```
^(http(s)?://)?[\w]+.com
```
This regex will match any string that includes http://, https://, or nothing followed by more than one word character further followed by .com. This would return the full string if the string is "https://google.com". (ie. https://google.com)

#### Non-Capturing Group

Used to group a set of characters or pattern together and will not capture anything in it when executed.

Example:
```
^(?:http(s)?://)?[\w]+.com
```
This regex will match any string that includes http://, https://, or nothing followed by more than one word character further followed by .com. This would return the string without the beginning if the string is "https://google.com". (ie. google.com)

### Bracket Expressions

| Expression | Description                    |
|:----------:|:-------------------------------|
| [abc]      | Match Character in Brackets    |
| [x-y]      | Match Character in Range       |
| [^x]       | Match Character not in Brackets|

#### Match Character in Brackets

Used to match any of the characters within the brackets.

Example:
```
^[aeiou]
```
This regex would pass if the string started with a vowel.

#### Match Character in Range

Used to match a character within a range of characters.

Example:
```
^[A-Z]
```
This regex would pass if the string started with an uppercase letter.

#### Match Character not in Brackets

Used to match any character not specified.

Example:
```
^[!@#$%^&*]+$
```
This regex would pass if the string didn't contain any special characters.

### Greedy and Lazy Match

#### Greedy Matches

Greedy matches are the default and what it means is if matching something is optional, then it will take as many as possible. For example:
```
[a-z]+
```
In this example, it will match on the first single occurence of a lowercase letter, but it will always take as many as it can before returning the match, eventhough the match is already satisfied by one single character.

#### Lazy Matches

Lazy matches can be enabled by adding a ? on the end of the quantifier. It will only take the bare minimum necessary pieces on the value it returns based on the pattern used. For example:
```
[a-z]{3,}?
```
In this example, it will match on the first occurences of 3 lowercase letters in a row, but it will only take the bare minimum it need before returning the match eventhough it could take an infinite number of characters.

### Boundaries

| Boundaries | Description       |
|:----------:|:------------------|
| \b         | Word boundary     |
| \B         | Non-word boundary |

#### Word Boundary

This matches any position where there is a word character on one side and not a word character on the other side.

Example:
```
\b[a-z]+\b
```
This regex would match any word that uses only lowercase characters.

#### Non-Word Boundary

This matches any position that is not a word boundary.

Example:
```
\Bcat
```
This regex would match any string that had cat in a word, where it wasn't at the start of the word, for example, tomcat or certificate. However, catfish would not work.

### Back-references

| References | Description            |
|:----------:|:-----------------------|
| \n         | Numbered Backreference |
| \k\<word\> | Named Backreference    |

#### Numbered Backreference

This is used to match a previous match's exact text for a specific grouping.

Example:
```
([a-zA-Z]+):([\d]+):[\2]
```
This regex would match a word followed by a colon, a number, another colon, and the exact same number found before.

#### Named Backreference

This is used to match a previous match's exact text for a named grouping.

Example:
```
([a-zA-Z]+):(?<value>):(\k<value>)
```
This regex will match the same as previous, but it doesn't have to be a number just whatever is between the two colons needs to match the final part after the colon.

### Look-ahead and Look-behind

| Lookarounds | Description        |
|:-----------:|:-------------------|
| (?=abc)     | Lookahead          |
| (?\<=abc)   | Lookbehind         |
| (?!abc)     | Negative Lookahead |
| (?\<!abc)   | Negative Lookahead |

#### Lookahead

This is used to ensure that a specific pattern follows the match you are looking for. What makes it special over just adding on a pattern on to the end is it won't consume additional characters on the end or include it in the output.
```
abc(?=def)
```
This would return a match if def followed abc, but it would only return the abc if it were executed.

#### Lookbehind

This is used to ensure that a specific pattern precedes the match you are looking for. What makes it special over just adding on a pattern on to the front is it won't consume additional characters on the front or include it in the output.
```
(?<=abc)def
```
This would return a match if abc precedes def, but it would only return the def if it were executed.

#### Negative Lookahead

This is used to ensure that a specific pattern does not follow the match you are looking for.
```
abc(?!def)
```
This would return a match only if def does not follow abc.

#### Negative Lookbehind

This is used to ensure that a specific pattern does not precede the match you are looking for.
```
(?<!abc)def
```
This would return a match only if def is not preceded by abc.

## Author

Github Name: tzeuch0922

Profile: https://github.com/tzeuch0922