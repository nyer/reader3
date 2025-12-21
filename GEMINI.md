# Gemini Project Context: reader3

## Project Overview

This project, "reader3," is a lightweight, self-hosted EPUB reader built with Python. The primary goal of the application is to allow users to read EPUB books one chapter at a time, making it easy to copy and paste chapter content into a Large Language Model (LLM) for collaborative reading and analysis.

The backend is a [FastAPI](https://fastapi.tiangolo.com/) application that serves a web-based interface. The frontend is rendered using [Jinja2](https://jinja.palletsprojects.com/en/3.1.x/) templates. The core EPUB processing logic is handled by the `ebooklib` and `BeautifulSoup4` libraries.

When an EPUB file is processed, it is converted into a structured Python object and saved as a `book.pkl` file in a dedicated data directory for that book. This data directory also contains any images extracted from the EPUB.

The main components of the project are:
- `server.py`: The main FastAPI application that serves the web interface.
- `reader3.py`: A script that contains the logic for parsing and processing EPUB files.
- `templates/`: A directory containing the Jinja2 templates for the web interface (`library.html` and `reader.html`).
- `pyproject.toml`: The project's configuration file, which lists the dependencies.

## Building and Running

The project uses [uv](https://docs.astral.sh/uv/) for dependency management and running the application.

### Processing a Book

To add a book to the library, run the `reader3.py` script with the path to an EPUB file. For example:

```bash
uv run reader3.py my_book.epub
```
This will create a `my_book_data` directory containing the processed book data.

### Running the Server

To run the web server, execute the `server.py` script:

```bash
uv run server.py
```
The server will be available at [http://localhost:8123](http://localhost:8123).

## Development Conventions

- The project follows a simple and straightforward structure, with the main application logic in `server.py` and the EPUB processing logic in `reader3.py`.
- The web interface is built using simple HTML, CSS, and a small amount of JavaScript for client-side interactions.
- The project does not have any explicit linting or formatting configurations, but the code is well-structured and easy to read.
- There are no tests included in the project.
