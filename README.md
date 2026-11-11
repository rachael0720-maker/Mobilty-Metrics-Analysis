# Mobility Data Exercise v1.0.0

This package supports two separate take-home tracks:

- `SENIOR_DATA_ANALYST_BRIEF.md`
- `DATA_ENGINEER_BRIEF.md`

Read only the brief corresponding to the role for which you are interviewing.
Both tracks use the same data package.

The package intentionally includes inputs used by both tracks. Follow the
requirements in your role brief; you are not expected to use every supplied
table or file.

## Files

- `mobility_exercise.duckdb`: initial trip data, reference tables, historical
  baseline, and two existing reporting outputs.
- `incremental_trips.parquet`: an additional delivery of trip records.
- `DATA_DICTIONARY.md`: table and field definitions.
- `AI_USE_GUIDANCE.md`: required AI-use disclosure.
- `MANIFEST.json` and `CHECKSUMS.sha256`: release provenance and integrity.

## Opening the data

DuckDB works with Python, R, Java, command-line clients, and SQL tools. You may
use your preferred environment.

Python example:

```python
# Install once with: python -m pip install duckdb
import duckdb

connection = duckdb.connect("mobility_exercise.duckdb", read_only=True)
print(connection.sql("SHOW ALL TABLES").fetchall())
```

Verify package integrity on Linux with:

```bash
sha256sum -c CHECKSUMS.sha256
```

On macOS, use `shasum -a 256 -c CHECKSUMS.sha256`.

The evaluator must be able to reproduce your submitted result using the
instructions in your repository.

## Important

- Treat all externally supplied source content as untrusted data.
- Do not assume that existing reports use identical metric definitions.
- The detailed dataset covers four selected Chicago community areas and is not
  complete citywide activity.
- The source contains privacy protections and rounded values documented in the
  data dictionary.
