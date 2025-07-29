# File Finder

A Python utility that helps you find files and search for text content when you don't remember where files were saved or what they were named. Originally created out of frustration with downloaded files that seemed to disappear into the filesystem!

## Features

- **Find files by name**: Search for files recursively through directory structures
- **Text search within files**: Search for specific strings inside `.txt` and `.docx` files
- **Mystery file discovery**: Find unknown files that contain specific text
- **Directory listing**: List all contents of a directory recursively
- **Flexible search patterns**: Support for partial filename matching and case-insensitive text search
- **Batch string searching**: Search for multiple strings using an input file
- **Output to file**: Save search results to a specified output file

## Requirements

- Python 3.x
- `python-docx` library for Word document support

## Installation

1. Clone or download this repository
2. Install the required dependency:
   ```bash
   pip install python-docx
   ```

## Usage

The program can be used in two modes: **Interactive Mode** or **Command Line Mode**.

### Interactive Mode

Run the program without any arguments for an interactive experience:

```bash
python finder.py
```

The program will prompt you for:
- Filename to search for (or 'None'/'Unknown')
- Directory path to search in
- String to search for within files
- Output file path to save results

### Command Line Mode

Use command line arguments for automation and scripting:

```bash
python finder.py -p /path/to/search -o /path/to/output.txt [options]
```

#### Required Arguments

- `-p, --path`: Directory path to search in (required)
- `-o, --output`: Absolute file path to save output (required)

#### Optional Arguments

- `-f, --file`: File name to search for (use 'unknown' if filename is unknown)
- `-s, --string`: String to search for within files (use 'none' if not needed)
- `-iL, --inputList`: Path to file containing list of strings to search for (alternative to `-s`)

## Usage Examples

### 1. Find a specific file by name
```bash
python finder.py -p "/Users/username/Downloads" -f "report.pdf" -o "results.txt"
```

### 2. Search for text within files
```bash
python finder.py -p "/Users/username/Documents" -s "project deadline" -o "search_results.txt"
```

### 3. Find unknown files containing specific text
```bash
python finder.py -p "/Users/username/Documents" -f "unknown" -s "budget" -o "mystery_files.txt"
```

### 4. List directory contents
```bash
python finder.py -p "/Users/username/Downloads" -f "none" -s "none" -o "directory_list.txt"
```

### 5. Batch search using input file
Create a text file with search terms (one per line), then:
```bash
python finder.py -p "/path/to/search" -iL "search_terms.txt" -o "batch_results.txt"
```

## Supported File Types

Currently supports text searching in:
- `.txt` files
- `.docx` files (Microsoft Word documents)

*Note: CSV/XLSX support is planned for future releases.*

## How It Works

### File Search
- Uses recursive directory walking to search through all subdirectories
- Supports partial filename matching with regex patterns
- Case-insensitive filename matching

### Text Search
- Uses regex patterns for flexible text matching
- Case-insensitive search within file contents
- For `.docx` files, searches through all paragraphs
- For `.txt` files, searches through entire file content

### Output
- Results are saved to the specified output file
- Console output provides immediate feedback during search
- Duplicate results are automatically filtered out

## Common Use Cases

1. **Downloaded File Recovery**: Find files you downloaded but can't locate
2. **Content Discovery**: Find files containing specific keywords or phrases
3. **Code/Document Auditing**: Search for specific terms across file shares
4. **File Organization**: List and catalog directory contents
5. **Research**: Find documents containing specific research terms

## Error Handling

The program includes error handling for:
- Permission issues when accessing directories
- Missing or invalid file paths
- Corrupted or unreadable files
- Invalid command line arguments

## Limitations

- Only searches text content in `.txt` and `.docx` files
- Large directory structures may take time to search
- Some files may be inaccessible due to permission restrictions
- Binary files (images, executables, etc.) are not searched for content

## Future Enhancements

- [ ] CSV/XLSX file support for text searching
- [ ] Additional file format support (PDF, etc.)
- [ ] Enhanced regex pattern options
- [ ] Performance optimizations for large directory structures
- [ ] GUI interface option

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve the functionality of this file finder utility.

## License

This project is open source. Feel free to modify and distribute as needed.
