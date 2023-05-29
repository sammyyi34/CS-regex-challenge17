# Regex Tutorial

As a web development student, I want a tutorial that explains a specific regex so that I can understand the search pattern it defines. This gist.md will help me improve my skills in web development and create more accurate search algorithms. This tutorial will explain anchors, quantifiers, grouping constructs, bracket expressions, character classes, the or operator, flags and character escapes.

## Summary

Regex, also known as regular expressions, are a fundamental tool in coding and search algorithms. As a beginner computer science student, it's important to understand their purpose and functionality. Regex allows us to define specific search patterns using sequences of characters. They can be used to locate particular character patterns or replace specific characters within a string. Regular expressions are also handy for validating user input. For instance, we can utilize a regex like /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/ to verify if user input matches a valid email address. This regex ensures that the input begins with any number of characters before the @ symbol, followed by a domain. Understanding these components helps us create powerful search algorithms and validate user input effectively.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

 Anchors are special characters used to specify the position of a match within a string. They essentially "anchor" the regex pattern to a specific location.

 There are two characters that are commonly used as anchors:

 - The `^` character represents the start of a string and matches everything that follows after the `^`.

 - The `$` character represents the end of a string and matches everything that preceeds the `$`.

 - In this example, `/^[hello][world]$/`, using the `^` anchor will include `[hello]` while the `$` anchor includes `[world]`.

### Quantifiers

Quantifiers set the limits of the string that your regex matches (or an individual section of the string). Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible.

Here's how bracket quantifiers work:

- `*` matches the preceding pattern zero or more times. For example, the pattern 'a' matches zero or more occurrences of the letter 'a'. So, it would match 'a', 'aa', 'aaa', and so on.

- `+` matches the preceding pattern one or more times. The example would be the same as the * however the + would not match an empty string.

- `?` specifies that the preceding element is optional and can occur zero or one time. For example, the pattern 'colou?r' matches both 'color' and 'colour'.

- `{}` can provide three different ways to set limits for a match:

  - `{ n }` matches the pattern exactly n number of times. For example, the pattern 'a{3}' matches exactly three occurrences of the letter 'a'. So, it would match 'aaa' but not 'aa' or 'aaaa'.

  - `{ n, }` matches the pattern at least n number of times. For example, the pattern 'a{3,}' will match 'aaa' and 'aaaa' because they have at least 3 occurences of 'a' but 'aa' would not match.

  - `{ n, x }` matches the pattern from a minimum of n number of times to a maximum of x number of times. For example, the pattern 'a{2,4}' matches two to four occurrences of the letter 'a'. So, it would match 'aa', 'aaa', and 'aaaa', but not 'a' or 'aaaaa'.

### Grouping Constructs

As regular expressions grow more complicated, grouping constructs allow you to check multiple parts of a string to determine that different sections fulfill different requirements. The primary way you group a section of a regex is by using `()`. Each section within parentheses is known as a subexpression.

The following example contains two grouping constructs or subexpressions:

`(123):(456)`

- The first subexpression is looking for a part of the string that matches the string "123" exactly.

- The second subexpression is looking for "456".

- In between the subexpressions, we have a colon (:). Thus, the string "123:457" would match, but the string "132:456" would not.

- Unlike bracket expressions, subexpressions look for an exact match unless they're told to do otherwise.

Grouping constructs have two primary categories: capturing and non-capturing. Capturing groups capture the matched character sequences for possible re-use (including a numbered backreference) while non-capturing groups do not. A grouping construct can be made non-capturing by adding the characters ?: at the beginning of an expression inside the parentheses.

### Bracket Expressions

Bracket expressions are anything inside a set of square brackets `[]` represents a range of characters that we want to match. They are also known as a positive character group, because they outline the characters we want to include.

Here's how bracket expressions work:

- Only square brackets `[]` enclose the characters you want to include in the character class. For example, `[abc]` matches any single occurrence of the characters 'a', 'b', or 'c'.

- A hyphen between alphanumeric characters `[-]` will specify a range of characters within the square brackets using a hyphen. For example, [a-z] matches any lowercase letter from 'a' to 'z'.

- Placing the `^` immediately after the opening square bracket turns the bracket expression into a negative character group, negating the character class. For instance, [^0-9] matches any character that is not a digit.

- Special character `[_-]` when a special character is placed within square brackets `[]`, it loses its special meaning and is treated as a regular character. For example "hello_world" would be a match because it contains an underscore and "123-456" would be a match because it contains a hyphen.

### Character Classes

Character classes are a way to define a group of characters in a regular expression. They allow you to match a single character against a predefined set of characters.

Here are some of the other common character classes:

- `.` matches any character except the newline character `(\n)`

- `\d` matches any Arabic numeral digit. This class is equivalent to the bracket expression `[0-9]`.

- `\w` matches any alphanumeric character from the basic Latin alphabet, including the underscore `(_)`. This class is equivalent to the bracket expression `[A-Za-z0-9_]`.

- `\s` matches a single whitespace character, including tabs and line breaks

Each of the last three character classes can be changed to perform an inverse match by capitalizing the letter character. For example, `\D` matches a non-digit character.

### The OR Operator

The or operator `|` enables you to define multiple options for a specific part of your pattern. Using the OR operator (|), the expression [abc] could be written as (a|b|c). 

Using our example in the grouping constructs section, we can take the original expression:

- `(123):(456)`

- And then use the OR operator to convert it to the following:

- `(1|2|3):(4|5|6)`

- Now, both of the strings "123:456" and "132:456" would match, as well as "1:6", but "456:123" would not.

### Flags

Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. Flags do not need to wrapped in a slash.

There are six optional flags that can be used, either separately or together and in any order, but these are the three you're most likely to encounter:

- Global search (g): allows the pattern to find all occurrences of a match within the input string, rather than stopping at the first match. For example, with the global flag enabled, the pattern `'/a/g'` would find and match all occurrences of the letter 'a' in the input string.

- Case-insensitive search (i): case should be ignored while attempting a match in a string For example, with the case-insensitive flag enabled, the pattern '/apple/i' would match 'apple', 'Apple', 'APple', and so on.

- Multi-line search (m): a multi-line input string should be treated as multiple lines

### Character Escapes

Character escapes allow you to match special characters or represent certain character types. They are denoted by a backslash () followed by a specific character or sequence.

For example, the open curly brace `{` is used to begin a quantifier, but adding a backslash before the open curly brace `\{` means that the regex should look for the open curly brace character instead of beginning to define a quantifier. This is common when looking for strings with special characters that are the same as a particular component of a regex.

## Author

Sammy Yi 

Github profile: https://github.com/sammyyi34