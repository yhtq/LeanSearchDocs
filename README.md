# LeanSearch API Docs
An easy-to-use API is provided to use our informal search service.
## Request URL
https://leansearch.net/api/search
## Request method
GET
## Request parameters
| name | required | type | description|
| ---- | -------- | ---- | -----------|
| query | True | string | The query string with maximum length 4096 characters|
| num_results| False | integer | Number of search results between 0 and 100. Default value is 50|

No body parameters.

## Response 
Normally, Response is a json that conforms to the following schema:
```json
{
    "type": "array",
    "items": {
        "type": "object",
        "properties": {
            "id": {
                "type": "integer",
                "description": "unique id of this item in our database",
                "examples": [
                    164679,
                    165855,
                    164680
                ]
            },
            "formal_name": {
                "type": "string",
                "description": "Lean name of this item",
                "examples": [
                    "rank_range_add_rank_ker",
                    "LinearMap.finrank_range_add_finrank_ker",
                    "rank_eq_of_surjective"
                ]
            },
            "formal_type": {
                "type": "string",
                "description": "Lean type of this item",
                "examples": [
                    "\u2200 {K : Type u} {V V\u2081 : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : AddCommGroup V\u2081] [inst_4 : Module K V\u2081] (f : V \u2192\u2097[K] V\u2081),   Module.rank K \u21a5(LinearMap.range f) + Module.rank K \u21a5(LinearMap.ker f) = Module.rank K V",
                    "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V] {V\u2082 : Type v'}   [inst_3 : AddCommGroup V\u2082] [inst_4 : Module K V\u2082] [inst_5 : FiniteDimensional K V] (f : V \u2192\u2097[K] V\u2082),   finrank K \u21a5(LinearMap.range f) + finrank K \u21a5(LinearMap.ker f) = finrank K V",
                    "\u2200 {K : Type u} {V V\u2081 : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : AddCommGroup V\u2081] [inst_4 : Module K V\u2081] (f : V \u2192\u2097[K] V\u2081),   Surjective \u21d1f \u2192 Module.rank K V = Module.rank K V\u2081 + Module.rank K \u21a5(LinearMap.ker f)"
                ]
            },
            "kind": {
                "type": "string",
                "description": "Lean kind(def, theorem, abbrev, ...) of this item",
                "examples": [
                    "theorem",
                    "theorem",
                    "theorem"
                ]
            },
            "file_name": {
                "type": "string",
                "description": "name of the Lean file containing this item",
                "examples": [
                    "Mathlib.LinearAlgebra.Basic",
                    "Mathlib.LinearAlgebra.FiniteSpan",
                    "Mathlib.LinearAlgebra.Basic"
                ]
            },
            "doc_url": {
                "type": "string",
                "description": "url of document of the Lean file containing this item",
                "examples": [
                    "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=rank_range_add_rank_ker#doc",
                    "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=LinearMap.finrank_range_add_finrank_ker#doc",
                    "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=rank_eq_of_surjective#doc"
                ]
            },
            "docstring": {
                "type": "string",
                "description": "docstring of this item",
                "examples": [
                    "The **rank-nullity theorem** ",
                    "rank-nullity theorem : the dimensions of the kernel and the range of a linear map add up to\nthe dimension of the source space. ",
                    ""
                ]
            }
        }
    }
}
```
Otherwise, one of the following error codes is returned:
- 422 Validation Error: Including sending request too quickly, the query being too long, etc. More information is provided in the response body.
- 500 Internal Server Error: An exception occurred on the server, please contact us to fix it.

### Response Examples
```json
[
    {
        "id": 164679,
        "formal_name": "rank_range_add_rank_ker",
        "formal_type": "\u2200 {K : Type u} {V V\u2081 : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : AddCommGroup V\u2081] [inst_4 : Module K V\u2081] (f : V \u2192\u2097[K] V\u2081),   Module.rank K \u21a5(LinearMap.range f) + Module.rank K \u21a5(LinearMap.ker f) = Module.rank K V",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.Basic",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=rank_range_add_rank_ker#doc",
        "docstring": "The **rank-nullity theorem** "
    },
    {
        "id": 165855,
        "formal_name": "LinearMap.finrank_range_add_finrank_ker",
        "formal_type": "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V] {V\u2082 : Type v'}   [inst_3 : AddCommGroup V\u2082] [inst_4 : Module K V\u2082] [inst_5 : FiniteDimensional K V] (f : V \u2192\u2097[K] V\u2082),   finrank K \u21a5(LinearMap.range f) + finrank K \u21a5(LinearMap.ker f) = finrank K V",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=LinearMap.finrank_range_add_finrank_ker#doc",
        "docstring": "rank-nullity theorem : the dimensions of the kernel and the range of a linear map add up to\nthe dimension of the source space. "
    },
    {
        "id": 164680,
        "formal_name": "rank_eq_of_surjective",
        "formal_type": "\u2200 {K : Type u} {V V\u2081 : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : AddCommGroup V\u2081] [inst_4 : Module K V\u2081] (f : V \u2192\u2097[K] V\u2081),   Surjective \u21d1f \u2192 Module.rank K V = Module.rank K V\u2081 + Module.rank K \u21a5(LinearMap.ker f)",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.Basic",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=rank_eq_of_surjective#doc",
        "docstring": ""
    },
    {
        "id": 164684,
        "formal_name": "rank_add_rank_split",
        "formal_type": "\u2200 {K : Type u} {V V\u2081 V\u2082 V\u2083 : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : AddCommGroup V\u2081] [inst_4 : Module K V\u2081] [inst_5 : AddCommGroup V\u2082] [inst_6 : Module K V\u2082]   [inst_7 : AddCommGroup V\u2083] [inst_8 : Module K V\u2083] (db : V\u2082 \u2192\u2097[K] V) (eb : V\u2083 \u2192\u2097[K] V) (cd : V\u2081 \u2192\u2097[K] V\u2082)   (ce : V\u2081 \u2192\u2097[K] V\u2083),   \u22a4 \u2264 LinearMap.range db \u2294 LinearMap.range eb \u2192     LinearMap.ker cd = \u22a5 \u2192       db \u2218\u2097 cd = eb \u2218\u2097 ce \u2192         (\u2200 (d : V\u2082) (e : V\u2083), db d = eb e \u2192 \u2203 c, cd c = d \u2227 ce c = e) \u2192           Module.rank K V + Module.rank K V\u2081 = Module.rank K V\u2082 + Module.rank K V\u2083",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.Basic",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=rank_add_rank_split#doc",
        "docstring": "This is mostly an auxiliary lemma for `Submodule.rank_sup_add_rank_inf_eq`. "
    },
    {
        "id": 165868,
        "formal_name": "LinearMap.ker_eq_bot_iff_range_eq_top_of_finrank_eq_finrank",
        "formal_type": "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V] {V\u2082 : Type v'}   [inst_3 : AddCommGroup V\u2082] [inst_4 : Module K V\u2082] [inst_5 : FiniteDimensional K V] [inst_6 : FiniteDimensional K V\u2082],   finrank K V = finrank K V\u2082 \u2192 \u2200 {f : V \u2192\u2097[K] V\u2082}, LinearMap.ker f = \u22a5 \u2194 LinearMap.range f = \u22a4",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=LinearMap.ker_eq_bot_iff_range_eq_top_of_finrank_eq_finrank#doc",
        "docstring": ""
    },
    {
        "id": 165910,
        "formal_name": "Module.End.ker_pow_eq_ker_pow_finrank_of_le",
        "formal_type": "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : FiniteDimensional K V] {f : End K V} {m : \u2115},   finrank K V \u2264 m \u2192 LinearMap.ker (f ^ m) = LinearMap.ker (f ^ finrank K V)",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=Module.End.ker_pow_eq_ker_pow_finrank_of_le#doc",
        "docstring": ""
    },
    {
        "id": 165804,
        "formal_name": "FiniteDimensional.finrank_eq_rank'",
        "formal_type": "\u2200 (K : Type u) (V : Type v) [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : FiniteDimensional K V], \u2191(finrank K V) = Module.rank K V",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=FiniteDimensional.finrank_eq_rank'#doc",
        "docstring": "In a finite-dimensional space, its dimension (seen as a cardinal) coincides with its\n`finrank`. This is a copy of `finrank_eq_rank _ _` which creates easier typeclass searches. "
    },
    {
        "id": 56577,
        "formal_name": "LinearIsometry.extend.proof_4",
        "formal_type": "\u2200 {\ud835\udd5c : Type u_2} [inst : IsROrC \ud835\udd5c] {V : Type u_1} [inst_1 : NormedAddCommGroup V] [inst_2 : InnerProductSpace \ud835\udd5c V]   [inst_3 : FiniteDimensional \ud835\udd5c V] {S : Submodule \ud835\udd5c V} (L : \u21a5S \u2192\u2097\u1d62[\ud835\udd5c] V),   finrank \ud835\udd5c \u21a5(LinearMap.range L.toLinearMap)\u15ee = finrank \ud835\udd5c \u21a5S\u15ee",
        "kind": "theorem",
        "file_name": "Mathlib.Analysis.Convex.Complex",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=LinearIsometry.extend.proof_4#doc",
        "docstring": ""
    },
    {
        "id": 165889,
        "formal_name": "finrank_eq_one_iff_of_nonzero",
        "formal_type": "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V] (v : V),   v \u2260 0 \u2192 (finrank K V = 1 \u2194 span K {v} = \u22a4)",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=finrank_eq_one_iff_of_nonzero#doc",
        "docstring": "A vector space with a nonzero vector `v` has dimension 1 iff `v` spans.\n"
    },
    {
        "id": 165851,
        "formal_name": "LinearMap.ker_eq_bot_iff_range_eq_top",
        "formal_type": "\u2200 {K : Type u} {V : Type v} [inst : DivisionRing K] [inst_1 : AddCommGroup V] [inst_2 : Module K V]   [inst_3 : FiniteDimensional K V] {f : V \u2192\u2097[K] V}, LinearMap.ker f = \u22a5 \u2194 LinearMap.range f = \u22a4",
        "kind": "theorem",
        "file_name": "Mathlib.LinearAlgebra.FiniteSpan",
        "doc_url": "https://leanprover-community.github.io/mathlib4_docs/find/?pattern=LinearMap.ker_eq_bot_iff_range_eq_top#doc",
        "docstring": ""
    }
]
```

### CURL Example
```bash
curl -X GET "https://leansearch.net/api/search?query=bezout%20theorem&num_results=3"
```

### Python Client Example
```python
import json
from typing import TypedDict
import httpx

class Response(TypedDict):
    id: int
    formal_name: str
    formal_type: str
    kind: str
    file_name: str
    doc_url: str
    docstring: str

def search(query: str, num_results: int = 50) -> list[Response]:
    client = httpx.Client()
    res = client.get(f"https://leansearch.net/api/search", 
                        params={             
                                "query": query,
                                "num_results": num_results
                        }
                        )
    assert res.status_code == 200, f'status code: {res.status_code}, message: {res.text}'
    return res.json()

async def search_async(query: str, num_results: int = 50) -> list[Response]:
    async with httpx.AsyncClient() as ac:
        res = await ac.get(f"https://leansearch.net/api/search", 
                            params={
                                    "query": query,
                                    "num_results": num_results
                            }
                            )
        assert res.status_code == 200, f'status code: {res.status_code}, message: {res.text}'
        return res.json()
    
```
